---
title: 備份裝置 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tape backup devices, about tape backup devices
- backup devices [SQL Server]
- disk backup devices [SQL Server]
- database backups [SQL Server], backup devices
- logical devices [SQL Server]
- backup devices [SQL Server], about backup devices
- backing up [SQL Server], backup devices
- removable media [SQL Server]
- network shares [SQL Server]
- backups [SQL Server], backup devices
- tape backup devices
- physical devices [SQL Server]
- backing up databases [SQL Server], backup devices
- devices [SQL Server]
ms.assetid: 35a8e100-3ff2-4844-a5da-dd088c43cba4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8abbba087679d263c00484764ecf445d6e5a006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710686"
---
# <a name="backup-devices-sql-server"></a><span data-ttu-id="d164e-102">備份裝置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d164e-102">Backup Devices (SQL Server)</span></span>
  <span data-ttu-id="d164e-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫上進行備份作業期間，備份的資料 (「備份」  ) 會寫入至實體備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-103">During a backup operation on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the backed up data (the *backup*) is written to a physical backup device.</span></span> <span data-ttu-id="d164e-104">當媒體集的第一個備份寫入此實體備份裝置時，此裝置就會初始化。</span><span class="sxs-lookup"><span data-stu-id="d164e-104">This physical backup device is initialized when the first backup in a media set is written to it.</span></span> <span data-ttu-id="d164e-105">單一媒體集是由一組一個或多個備份裝置上的備份所組成。</span><span class="sxs-lookup"><span data-stu-id="d164e-105">The backups on a set of one or more backup devices compose a single media set.</span></span>  
  
 <span data-ttu-id="d164e-106">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="d164e-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="d164e-107">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="d164e-107">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="d164e-108">使用磁片備份裝置</span><span class="sxs-lookup"><span data-stu-id="d164e-108">Using Disk Backup Devices</span></span>](#DiskBackups)  
  
-   [<span data-ttu-id="d164e-109">使用磁帶裝置</span><span class="sxs-lookup"><span data-stu-id="d164e-109">Using Tape Devices</span></span>](#TapeDevices)  
  
-   [<span data-ttu-id="d164e-110">使用邏輯備份裝置</span><span class="sxs-lookup"><span data-stu-id="d164e-110">Using a Logical Backup Device</span></span>](#LogicalBackupDevice)  
  
-   [<span data-ttu-id="d164e-111">鏡像備份媒體集</span><span class="sxs-lookup"><span data-stu-id="d164e-111">Mirrored Backup Media Sets</span></span>](#MirroredMediaSets)  
  
-   [<span data-ttu-id="d164e-112">封存 SQL Server 備份</span><span class="sxs-lookup"><span data-stu-id="d164e-112">Archiving SQL Server Backups</span></span>](#Archiving)  
  
-   [<span data-ttu-id="d164e-113">相關工作</span><span class="sxs-lookup"><span data-stu-id="d164e-113">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="d164e-114">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="d164e-114">Terms and Definitions</span></span>  
 <span data-ttu-id="d164e-115">備份磁碟</span><span class="sxs-lookup"><span data-stu-id="d164e-115">backup disk</span></span>  
 <span data-ttu-id="d164e-116">包含一個或多個備份檔案的硬碟或其他磁碟儲存媒體。</span><span class="sxs-lookup"><span data-stu-id="d164e-116">A hard disk or other disk storage media that contains one or more backup files.</span></span> <span data-ttu-id="d164e-117">備份檔案是一般作業系統檔案。</span><span class="sxs-lookup"><span data-stu-id="d164e-117">A backup file is a regular operating system file.</span></span>  
  
 <span data-ttu-id="d164e-118">媒體集</span><span class="sxs-lookup"><span data-stu-id="d164e-118">media set</span></span>  
 <span data-ttu-id="d164e-119">按順序排列的備份媒體、磁帶或磁碟檔案集合，而且它會使用備份裝置的固定類型和編號。</span><span class="sxs-lookup"><span data-stu-id="d164e-119">An ordered collection of backup media, tapes or disk files, that uses a fixed type and number of backup devices.</span></span> <span data-ttu-id="d164e-120">如需媒體集的詳細資訊，請參閱 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d164e-120">For more information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="d164e-121">實體備份裝置</span><span class="sxs-lookup"><span data-stu-id="d164e-121">physical backup device</span></span>  
 <span data-ttu-id="d164e-122">磁帶機或作業系統所提供的磁碟檔案。</span><span class="sxs-lookup"><span data-stu-id="d164e-122">Either a tape drive or a disk file that is provided by the operating system.</span></span> <span data-ttu-id="d164e-123">備份可以寫入 1 到 64 部備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-123">A backup can be written to from 1 to 64 backup devices.</span></span> <span data-ttu-id="d164e-124">如果備份需要多部備份裝置，這些裝置都必須對應至單一裝置類型 (磁碟或磁帶)。</span><span class="sxs-lookup"><span data-stu-id="d164e-124">If a backup requires multiple backup devices, the devices all must correspond to a single type of device (disk or tape).</span></span>  
  
 <span data-ttu-id="d164e-125">除了磁碟或磁帶之外，SQL Server 備份也可以寫入 Azure Blob 儲存體服務。</span><span class="sxs-lookup"><span data-stu-id="d164e-125">SQL Server Backups can also be written to Azure Blob storage service in addition to disk or tape.</span></span>  
  
##  <a name="using-disk-backup-devices"></a><a name="DiskBackups"></a><span data-ttu-id="d164e-126">使用磁片備份裝置</span><span class="sxs-lookup"><span data-stu-id="d164e-126">Using Disk Backup Devices</span></span>  
 <span data-ttu-id="d164e-127">**本節內容：**</span><span class="sxs-lookup"><span data-stu-id="d164e-127">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="d164e-128">使用實體名稱來指定備份檔案 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d164e-128">Specifying a Backup File by Using Its Physical Name (Transact-SQL)</span></span>](#BackupFileUsingPhysicalName)  
  
-   [<span data-ttu-id="d164e-129">指定磁碟備份檔案的路徑</span><span class="sxs-lookup"><span data-stu-id="d164e-129">Specifying the Path of a Disk Backup File</span></span>](#BackupFileDiskPath)  
  
-   [<span data-ttu-id="d164e-130">備份至網路共用上的檔案</span><span class="sxs-lookup"><span data-stu-id="d164e-130">Backing Up to a File on a Network Share</span></span>](#NetworkShare)  
  
 <span data-ttu-id="d164e-131">如果備份作業將備份附加至媒體集時，磁碟檔案填滿，備份作業就會失敗。</span><span class="sxs-lookup"><span data-stu-id="d164e-131">If a disk file fills while a backup operation is appending a backup to the media set, the backup operation fails.</span></span> <span data-ttu-id="d164e-132">由於備份檔案的大小上限是由磁碟裝置上的可用磁碟空間決定，所以備份磁碟裝置的適當大小要根據您的備份大小而定。</span><span class="sxs-lookup"><span data-stu-id="d164e-132">The maximum size of a backup file is determined by the free disk space available on the disk device; therefore, the appropriate size for a backup disk device depends on the size of your backups.</span></span>  
  
 <span data-ttu-id="d164e-133">磁碟備份裝置可以是簡單的磁碟裝置，例如 ATA 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="d164e-133">A disk backup device could be a simple disk device, such as an ATA drive.</span></span> <span data-ttu-id="d164e-134">或者，您也可以使用可熱抽換的 (Hot-swappable) 磁碟機，以便您將磁碟機上寫滿的磁碟直接了當地更換成空的磁碟。</span><span class="sxs-lookup"><span data-stu-id="d164e-134">Alternatively, you could use a hot-swappable disk drive that would let you transparently replace a full disk on the drive with an empty disk.</span></span> <span data-ttu-id="d164e-135">備份磁碟可以是伺服器上的本機磁碟，也可以是屬於共用網路資源的遠端磁碟。</span><span class="sxs-lookup"><span data-stu-id="d164e-135">A backup disk can be a local disk on the server or a remote disk that is a shared network resource.</span></span> <span data-ttu-id="d164e-136">如需有關如何使用遠端磁碟的詳細資訊，請參閱本主題後面的＜ [備份至網路共用上的檔案](#NetworkShare)＞。</span><span class="sxs-lookup"><span data-stu-id="d164e-136">For information about how to use a remote disk, see [Backing Up to a File on a Network Share](#NetworkShare), later in this topic.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d164e-137">管理工具在處理磁碟備份裝置時相當有彈性，因為它們會自動在磁碟檔案上產生具有時間戳記的名稱。</span><span class="sxs-lookup"><span data-stu-id="d164e-137">management tools are very flexible at handling disk backup devices because they automatically generate a time-stamped name on the disk file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d164e-138">我們建議備份磁碟應該與資料庫資料和記錄磁碟使用不同的磁碟。</span><span class="sxs-lookup"><span data-stu-id="d164e-138">We recommend that a backup disk be a different disk than the database data and log disks.</span></span> <span data-ttu-id="d164e-139">為了確保您可以在資料或記錄磁碟故障時存取備份，這樣做有其必要。</span><span class="sxs-lookup"><span data-stu-id="d164e-139">This is necessary to make sure that you can access the backups if the data or log disk fails.</span></span>  
  
###  <a name="specifying-a-backup-file-by-using-its-physical-name-transact-sql"></a><a name="BackupFileUsingPhysicalName"></a><span data-ttu-id="d164e-140">使用 (Transact-sql 的機構名稱來指定備份檔案) </span><span class="sxs-lookup"><span data-stu-id="d164e-140">Specifying a Backup File by Using Its Physical Name (Transact-SQL)</span></span>  
 <span data-ttu-id="d164e-141">使用實體裝置名稱來指定備份檔案的基本 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 語法為：</span><span class="sxs-lookup"><span data-stu-id="d164e-141">The basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) syntax for specifying a backup file by using its physical device name is:</span></span>  
  
 <span data-ttu-id="d164e-142">BACKUP DATABASE *database_name*</span><span class="sxs-lookup"><span data-stu-id="d164e-142">BACKUP DATABASE *database_name*</span></span>  
  
 <span data-ttu-id="d164e-143">TO DISK **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="d164e-143">TO DISK **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="d164e-144">例如：</span><span class="sxs-lookup"><span data-stu-id="d164e-144">For example:</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';  
GO  
```  
  
 <span data-ttu-id="d164e-145">若要在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式中指定實體磁碟裝置，基本語法為：</span><span class="sxs-lookup"><span data-stu-id="d164e-145">To specify a physical disk device in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, the basic syntax is:</span></span>  
  
 <span data-ttu-id="d164e-146">RESTORE { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="d164e-146">RESTORE { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="d164e-147">FROM DISK **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="d164e-147">FROM DISK **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="d164e-148">例如，</span><span class="sxs-lookup"><span data-stu-id="d164e-148">For example,</span></span>  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';   
```  
  
###  <a name="specifying-the-path-of-a-disk-backup-file"></a><a name="BackupFileDiskPath"></a><span data-ttu-id="d164e-149">指定磁片備份檔案的路徑</span><span class="sxs-lookup"><span data-stu-id="d164e-149">Specifying the Path of a Disk Backup File</span></span>  
 <span data-ttu-id="d164e-150">指定備份檔案時，您應該輸入完整路徑及檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d164e-150">When you are specifying a backup file, you should enter its full path and file name.</span></span> <span data-ttu-id="d164e-151">當您要備份至檔案時，如果僅指定檔案名稱或相對路徑，便會將備份檔案放在預設的備份目錄中。</span><span class="sxs-lookup"><span data-stu-id="d164e-151">If you specify only the file name or a relative path when you are backing up to a file, the backup file is put in the default backup directory.</span></span> <span data-ttu-id="d164e-152">預設的備份目錄為 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup，其中 *n* 是伺服器執行個體的編號。</span><span class="sxs-lookup"><span data-stu-id="d164e-152">The default backup directory is C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup, where *n* is the number of the server instance.</span></span> <span data-ttu-id="d164e-153">因此，對預設的伺服器執行個體而言，其預設備份目錄為：C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup。</span><span class="sxs-lookup"><span data-stu-id="d164e-153">Therefore, for the default server instance, the default backup directory is: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup.</span></span>  
  
 <span data-ttu-id="d164e-154">若要避免模稜兩可的情形 (特別是在指令碼中)，建議您在每個 DISK 子句中明確指定備份目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="d164e-154">To avoid ambiguity, especially in scripts, we recommend that you explicitly specify the path of the backup directory in every DISK clause.</span></span> <span data-ttu-id="d164e-155">不過，當您使用「查詢編輯器」時，這就不是那麼重要。</span><span class="sxs-lookup"><span data-stu-id="d164e-155">However, this is less important when you are using Query Editor.</span></span> <span data-ttu-id="d164e-156">在這種情況下，如果您確定備份檔案是在預設的備份目錄中，即可省略 DISK 子句中的路徑。</span><span class="sxs-lookup"><span data-stu-id="d164e-156">In that case, if you are sure that the backup file resides in the default backup directory, you can omit the path from a DISK clause.</span></span> <span data-ttu-id="d164e-157">例如，下列 `BACKUP` 陳述式會將 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫備份到預設備份目錄。</span><span class="sxs-lookup"><span data-stu-id="d164e-157">For example, the following `BACKUP` statement backs up the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to the default backup directory.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'AdventureWorks2012.bak';  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d164e-158">預設位置會儲存在 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer** 下的 **BackupDirectory**登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="d164e-158">The default location is stored in the **BackupDirectory** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer**.</span></span>  
  
###  <a name="backing-up-to-a-file-on-a-network-share"></a><a name="NetworkShare"></a><span data-ttu-id="d164e-159">備份至網路共用上的檔案</span><span class="sxs-lookup"><span data-stu-id="d164e-159">Backing Up to a File on a Network Share</span></span>  
 <span data-ttu-id="d164e-160">為了讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取遠端磁碟檔案， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶必須具有網路共用的存取權。</span><span class="sxs-lookup"><span data-stu-id="d164e-160">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to access a remote disk file, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account must have access to the network share.</span></span> <span data-ttu-id="d164e-161">這包括具有讓備份作業寫入網路共用以及讓還原作業從中讀取所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d164e-161">This includes having the permissions needed for backup operations to write to the network share and for restore operations to read from it.</span></span> <span data-ttu-id="d164e-162">網路磁碟機和權限的可用性會根據 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務執行的內容而定：</span><span class="sxs-lookup"><span data-stu-id="d164e-162">The availability of network drives and permissions depends on the context is which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is running:</span></span>  
  
-   <span data-ttu-id="d164e-163">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在網域使用者帳戶下執行時，若要備份至網路磁碟機，共用磁碟機就必須對應成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在執行之工作階段中的網路磁碟機。</span><span class="sxs-lookup"><span data-stu-id="d164e-163">To back up to a network drive when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in a domain user account, the shared drive must be mapped as a network drive in the session where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="d164e-164">如果是從命令列啟動 Sqlservr.exe， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 便看得到您登入工作階段中已對應的所有網路磁碟機。</span><span class="sxs-lookup"><span data-stu-id="d164e-164">If you start Sqlservr.exe from command line, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sees any network drives you have mapped in your login session.</span></span>  
  
-   <span data-ttu-id="d164e-165">不過，如果 Sqlservr.exe 是以服務方式執行，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在另一個與登入工作階段無關的工作階段中執行。</span><span class="sxs-lookup"><span data-stu-id="d164e-165">When you run Sqlservr.exe as a service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs in a separate session that has no relation to your login session.</span></span> <span data-ttu-id="d164e-166">服務執行的工作階段可擁有自己的對應磁碟機 (只是它通常沒有)。</span><span class="sxs-lookup"><span data-stu-id="d164e-166">The session in which a service runs can have its own mapped drives, although it usually does not.</span></span>  
  
-   <span data-ttu-id="d164e-167">您可以使用電腦帳戶代替網域使用者來與網路服務帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="d164e-167">You can connect with the network service account by using the computer account instead of a domain user.</span></span> <span data-ttu-id="d164e-168">若要允許從特定電腦備份至共用磁碟機，請將存取權授與電腦帳戶。</span><span class="sxs-lookup"><span data-stu-id="d164e-168">To enable backups from specific computers to a shared drive, grant access to the computer accounts.</span></span> <span data-ttu-id="d164e-169">只要正在寫入備份的 Sqlservr.exe 處理序具有存取權，傳送 BACKUP 命令的使用者是否具有存取權便無關了。</span><span class="sxs-lookup"><span data-stu-id="d164e-169">As long as the Sqlservr.exe process that is writing the backup has access, it is irrelevant whether the user sending the BACKUP command has access.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d164e-170">透過網路備份資料可能會受到網路問題的影響。因此，我們建議您在使用遠端磁碟時，於備份作業完成後進行驗證。</span><span class="sxs-lookup"><span data-stu-id="d164e-170">Backing up data over a network can be subject to network errors; therefore, we recommend that when you are using a remote disk you verify the backup operation after it finishes.</span></span> <span data-ttu-id="d164e-171">如需詳細資訊，請參閱 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d164e-171">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
#### <a name="specifying-a-universal-naming-convention-unc-name"></a><span data-ttu-id="d164e-172">指定通用命名慣例 (UNC) 名稱</span><span class="sxs-lookup"><span data-stu-id="d164e-172">Specifying a Universal Naming Convention (UNC) Name</span></span>  
 <span data-ttu-id="d164e-173">若要在備份或還原命令中指定網路共用，您應該要使用備份裝置檔案的完整通用命名慣例 (UNC) 名稱。</span><span class="sxs-lookup"><span data-stu-id="d164e-173">To specify a network share in a backup or restore command, you should use the fully qualified universal naming convention (UNC) name of the file for the backup device.</span></span> <span data-ttu-id="d164e-174">UNC 名稱的格式為 **\\\\** <系統名稱>  **\\** <共用名稱>  **\\** <路徑>  **\\** <檔案名稱>  。</span><span class="sxs-lookup"><span data-stu-id="d164e-174">A UNC name has the form **\\\\**_Systemname_**\\**_ShareName_**\\**_Path_**\\**_FileName_.</span></span>  
  
 <span data-ttu-id="d164e-175">例如：</span><span class="sxs-lookup"><span data-stu-id="d164e-175">For example:</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = '\\BackupSystem\BackupDisk1\AW_backups\AdventureWorksData.Bak';  
GO  
```  
  
##  <a name="using-tape-devices"></a><a name="TapeDevices"></a><span data-ttu-id="d164e-176">使用磁帶裝置</span><span class="sxs-lookup"><span data-stu-id="d164e-176">Using Tape Devices</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d164e-177">未來的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本中將會移除磁帶備份裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="d164e-177">Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d164e-178">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d164e-178">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="d164e-179">**本節內容：**</span><span class="sxs-lookup"><span data-stu-id="d164e-179">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="d164e-180">使用實體名稱來指定備份磁帶 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d164e-180">Specifying a Backup Tape by Using Its Physical Name (Transact-SQL)</span></span>](#BackupTapeUsingPhysicalName)  
  
-   [<span data-ttu-id="d164e-181"> (Transact-sql) 的磁帶特定備份和還原選項</span><span class="sxs-lookup"><span data-stu-id="d164e-181">Tape-Specific BACKUP and RESTORE Options (Transact-SQL)</span></span>](#TapeOptions)  
  
-   [<span data-ttu-id="d164e-182">管理開啟的磁帶</span><span class="sxs-lookup"><span data-stu-id="d164e-182">Managing Open Tapes</span></span>](#OpenTapes)  
  
 <span data-ttu-id="d164e-183">磁帶機必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 作業系統所支援的，才能將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 資料備份到磁帶中。</span><span class="sxs-lookup"><span data-stu-id="d164e-183">Backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data to tape requires that the tape drive or drives be supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows operating system.</span></span> <span data-ttu-id="d164e-184">此外，對指定的磁帶機而言，我們建議您僅使用磁帶機製造商所建議的磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-184">Additionally, for the given tape drive, we recommend that you use only tapes recommended by the drive manufacturer.</span></span> <span data-ttu-id="d164e-185">如需有關如何安裝磁帶機的詳細資訊，請參閱 Windows 作業系統的文件。</span><span class="sxs-lookup"><span data-stu-id="d164e-185">For more information about how to install a tape drive, see the documentation for the Windows operating system.</span></span>  
  
 <span data-ttu-id="d164e-186">使用磁帶機時，備份作業可能會填滿一捲磁帶，然後繼續寫入另一捲磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-186">When a tape drive is used, a backup operation may fill one tape and continue onto another tape.</span></span> <span data-ttu-id="d164e-187">每個磁帶都含有媒體標頭。</span><span class="sxs-lookup"><span data-stu-id="d164e-187">Each tape contains a media header.</span></span> <span data-ttu-id="d164e-188">第一個使用的媒體稱為 *「初始磁帶」* 。</span><span class="sxs-lookup"><span data-stu-id="d164e-188">The first media used is called the *initial tape*.</span></span> <span data-ttu-id="d164e-189">後續的磁帶都稱為 *接續磁帶* ，每捲磁帶都有一個媒體序號，後面的磁帶編號比前面的高。</span><span class="sxs-lookup"><span data-stu-id="d164e-189">Each successive tape is known as a *continuation tape* and has a media sequence number that is one higher than the previous tape.</span></span> <span data-ttu-id="d164e-190">例如，與四個磁帶裝置相關聯的媒體集，內含至少四捲初始磁帶；而如果一捲磁帶裝不下整個資料庫，則還會有四捲接續磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-190">For example, a media set associated with four tape devices contains at least four initial tapes (and, if the database does not fit, four series of continuation tapes).</span></span> <span data-ttu-id="d164e-191">附加備份組的時候，您必須掛載整組媒體中的最後一捲磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-191">When appending a backup set, you must mount the last tape in the series.</span></span> <span data-ttu-id="d164e-192">若未掛載最後一捲磁帶， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 往前掃描到掛載磁帶的結尾時，便會要求您更換磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-192">If the last tape is not mounted, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] scans forward to the end of the mounted tape and then requires that you change the tape.</span></span> <span data-ttu-id="d164e-193">此時，請掛載最後一捲磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-193">At that point, mount the last tape.</span></span>  
  
 <span data-ttu-id="d164e-194">使用磁帶備份裝置就像使用磁碟裝置一樣，但有以下例外情況：</span><span class="sxs-lookup"><span data-stu-id="d164e-194">Tape backup devices are used like disk devices, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="d164e-195">磁帶裝置必須在實體上連接至執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的電腦。</span><span class="sxs-lookup"><span data-stu-id="d164e-195">The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d164e-196">不支援備份至遠端磁帶裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-196">Backing up to remote tape devices is not supported.</span></span>  
  
-   <span data-ttu-id="d164e-197">如果在備份作業進行時磁帶備份裝置填滿，但還必須寫入更多資料的話， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會提示換新磁帶，並於載入新磁帶後繼續進行備份作業。</span><span class="sxs-lookup"><span data-stu-id="d164e-197">If a tape backup device is filled during the backup operation, but more data still must be written, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prompts for a new tape and continues the backup operation after a new tape is loaded.</span></span>  
  
###  <a name="specifying-a-backup-tape-by-using-its-physical-name-transact-sql"></a><a name="BackupTapeUsingPhysicalName"></a><span data-ttu-id="d164e-198">使用 (Transact-sql 的機構名稱來指定備份磁帶) </span><span class="sxs-lookup"><span data-stu-id="d164e-198">Specifying a Backup Tape by Using Its Physical Name (Transact-SQL)</span></span>  
 <span data-ttu-id="d164e-199">使用磁帶機之實體裝置名稱來指定備份磁帶的基本 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 語法為：</span><span class="sxs-lookup"><span data-stu-id="d164e-199">The basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) syntax for specifying a backup tape using the physical device name of the tape drive is:</span></span>  
  
 <span data-ttu-id="d164e-200">BACKUP { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="d164e-200">BACKUP { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="d164e-201">TO TAPE **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="d164e-201">TO TAPE **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="d164e-202">例如：</span><span class="sxs-lookup"><span data-stu-id="d164e-202">For example:</span></span>  
  
```  
BACKUP LOG AdventureWorks2012   
   TO TAPE = '\\.\tape0';  
GO  
```  
  
 <span data-ttu-id="d164e-203">若要在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式中指定實體磁帶裝置，基本語法為：</span><span class="sxs-lookup"><span data-stu-id="d164e-203">To specify a physical tape device in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, the basic syntax is:</span></span>  
  
 <span data-ttu-id="d164e-204">RESTORE { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="d164e-204">RESTORE { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="d164e-205">FROM TAPE **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="d164e-205">FROM TAPE **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
###  <a name="tape-specific-backup-and-restore-options-transact-sql"></a><a name="TapeOptions"></a> <span data-ttu-id="d164e-206">(Transact-sql) 的磁帶特定備份和還原選項</span><span class="sxs-lookup"><span data-stu-id="d164e-206">Tape-Specific BACKUP and RESTORE Options (Transact-SQL)</span></span>  
 <span data-ttu-id="d164e-207">為了方便磁帶管理作業，BACKUP 陳述式提供了下列磁帶專用的選項：</span><span class="sxs-lookup"><span data-stu-id="d164e-207">To facilitate tape management, the BACKUP statement provides the following tape-specific options:</span></span>  
  
-   <span data-ttu-id="d164e-208">{ NOUNLOAD | **UNLOAD** }</span><span class="sxs-lookup"><span data-stu-id="d164e-208">{ NOUNLOAD | **UNLOAD** }</span></span>  
  
     <span data-ttu-id="d164e-209">您可以控制在備份或還原作業之後，備份磁帶是否會自動從磁帶機卸載。</span><span class="sxs-lookup"><span data-stu-id="d164e-209">You can control whether a backup tape is unloaded automatically from the tape drive after a backup or restore operation.</span></span> <span data-ttu-id="d164e-210">UNLOAD/NOUNLOAD 是工作階段設定，在工作階段的存留期間會一直保持不變，直到指定其他設定來進行重設為止。</span><span class="sxs-lookup"><span data-stu-id="d164e-210">UNLOAD/NOUNLOAD is a session setting that persists for the life of the session or until it is reset by specifying the alternative.</span></span>  
  
-   <span data-ttu-id="d164e-211">{ **REWIND** | NOREWIND }</span><span class="sxs-lookup"><span data-stu-id="d164e-211">{ **REWIND** | NOREWIND }</span></span>  
  
     <span data-ttu-id="d164e-212">您可以控制在備份或還原作業之後， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會將磁帶保持在開啟狀態，還是會在磁帶填滿之後，釋出並倒轉磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-212">You can control whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keeps the tape remains open after the backup or restore operation or releases and rewinds the tape after it fills.</span></span> <span data-ttu-id="d164e-213">預設行為是倒轉磁帶 (REWIND)。</span><span class="sxs-lookup"><span data-stu-id="d164e-213">The default behavior is to rewind the tape (REWIND).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d164e-214">如需 BACKUP 語法和引數的詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d164e-214">For more information about the BACKUP syntax and arguments, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="d164e-215">如需 RESTORE 語法和引數的詳細資訊，請分別參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 和 [RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d164e-215">For more information about the RESTORE syntax and arguments, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql), respectively.</span></span>  
  
###  <a name="managing-open-tapes"></a><a name="OpenTapes"></a><span data-ttu-id="d164e-216">管理開啟的磁帶</span><span class="sxs-lookup"><span data-stu-id="d164e-216">Managing Open Tapes</span></span>  
 <span data-ttu-id="d164e-217">若要檢視開啟的磁帶裝置清單以及掛載要求的狀態，請查詢 [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) 動態管理檢視。</span><span class="sxs-lookup"><span data-stu-id="d164e-217">To view a list of open tape devices and the status of mount requests, query the [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) dynamic management view.</span></span> <span data-ttu-id="d164e-218">這個檢視顯示所有開啟的磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-218">This view shows all the open tapes.</span></span> <span data-ttu-id="d164e-219">這包括正在等待下一個 BACKUP 或 RESTORE 作業而暫時閒置的使用中磁帶。</span><span class="sxs-lookup"><span data-stu-id="d164e-219">These include in-use tapes that are temporarily idle while they wait for the next BACKUP or RESTORE operation.</span></span>  
  
 <span data-ttu-id="d164e-220">如果磁帶不慎保持在開啟狀態，釋放磁帶最快速的方式就是使用下列命令：RESTORE REWINDONLY FROM TAPE **=** _backup_device_name_。</span><span class="sxs-lookup"><span data-stu-id="d164e-220">If a tape has been accidentally left open, the fastest way to release the tape is by using the following command: RESTORE REWINDONLY FROM TAPE **=**_backup_device_name_.</span></span> <span data-ttu-id="d164e-221">如需詳細資訊，請參閱 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d164e-221">For more information, see [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql).</span></span>  
  
## <a name="using-the-azure-blob-storage-service"></a><span data-ttu-id="d164e-222">使用 Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="d164e-222">Using the Azure Blob Storage Service</span></span>  
 <span data-ttu-id="d164e-223">SQL Server 備份可以寫入 Azure Blob 儲存體服務。</span><span class="sxs-lookup"><span data-stu-id="d164e-223">SQL Server Backups can be written to the Azure Blob Storage Service.</span></span>  <span data-ttu-id="d164e-224">如需有關如何使用 Azure Blob 儲存體服務進行備份的詳細資訊，請參閱[使用 Azure Blob 儲存體服務 SQL Server 備份和還原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="d164e-224">For more information on how to use the Azure Blob storage service for your backups, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
##  <a name="using-a-logical-backup-device"></a><a name="LogicalBackupDevice"></a><span data-ttu-id="d164e-225">使用邏輯備份裝置</span><span class="sxs-lookup"><span data-stu-id="d164e-225">Using a Logical Backup Device</span></span>  
 <span data-ttu-id="d164e-226">*「邏輯備份裝置」* (Logical backup device) 是選擇性的使用者自訂名稱，而且它會指向特定的實體備份裝置 (磁碟檔案或磁帶機)。</span><span class="sxs-lookup"><span data-stu-id="d164e-226">A *logical backup device* is an optional, user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span> <span data-ttu-id="d164e-227">邏輯備份裝置可讓您在參考對應的實體備份裝置時，使用間接取值。</span><span class="sxs-lookup"><span data-stu-id="d164e-227">A logical backup device lets you use indirection when referencing the corresponding physical backup device.</span></span>  
  
 <span data-ttu-id="d164e-228">定義邏輯備份裝置會需要將邏輯名稱指派給實體裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-228">Defining a logical backup device involves assigning a logical name to a physical device.</span></span> <span data-ttu-id="d164e-229">例如，您可以將邏輯裝置 AdventureWorksBackups 定義為指向 Z:\SQLServerBackups\AdventureWorks2012.bak 檔案或 \\\\.\tape0 磁帶機。</span><span class="sxs-lookup"><span data-stu-id="d164e-229">For example, a logical device, AdventureWorksBackups, could be defined to point to the Z:\SQLServerBackups\AdventureWorks2012.bak file or the \\\\.\tape0 tape drive.</span></span> <span data-ttu-id="d164e-230">備份和還原命令便可以將 AdventureWorksBackups 指定為備份裝置，而不需設定 DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' 或 TAPE = '\\\\.\tape0'。</span><span class="sxs-lookup"><span data-stu-id="d164e-230">Backup and restore commands can then specify AdventureWorksBackups as the backup device, instead of DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' or TAPE = '\\\\.\tape0'.</span></span>  
  
 <span data-ttu-id="d164e-231">邏輯裝置名稱在伺服器執行個體上所有邏輯備份裝置中都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d164e-231">The logical device name must be unique among all the logical backup devices on the server instance.</span></span> <span data-ttu-id="d164e-232">若要檢視現有的邏輯裝置名稱，請查詢 [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="d164e-232">To view the existing logical device names, query the [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) catalog view.</span></span> <span data-ttu-id="d164e-233">這個檢視會顯示每個邏輯備份裝置的名稱，並且描述對應實體備份裝置的類型及實體檔案名稱或路徑。</span><span class="sxs-lookup"><span data-stu-id="d164e-233">This view displays the name of each logical backup device and describes the type and physical file name or path of the corresponding physical backup device.</span></span>  
  
 <span data-ttu-id="d164e-234">定義邏輯備份裝置之後，您就可以在 BACKUP 或 RESTORE 命令中指定邏輯備份裝置來替代裝置的實體名稱。</span><span class="sxs-lookup"><span data-stu-id="d164e-234">After a logical backup device is defined, in a BACKUP or RESTORE command, you can specify the logical backup device instead of the physical name of the device.</span></span> <span data-ttu-id="d164e-235">例如，下列陳述式會將 `AdventureWorks2012` 資料庫備份到 `AdventureWorksBackups` 邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-235">For example, the following statement backs up the `AdventureWorks2012` database to the `AdventureWorksBackups` logical backup device.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO AdventureWorksBackups;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d164e-236">在指定的 BACKUP 或 RESTORE 陳述式中，邏輯備份裝置名稱和對應的實體備份裝置名稱是可互換的。</span><span class="sxs-lookup"><span data-stu-id="d164e-236">In a given BACKUP or RESTORE statement, the logical backup device name and the corresponding physical backup device name are interchangeable.</span></span>  
  
 <span data-ttu-id="d164e-237">使用邏輯備份裝置的其中一項優點是，它比冗長的路徑名稱更容易使用。</span><span class="sxs-lookup"><span data-stu-id="d164e-237">One advantage of using a logical backup device is that it is simpler to use than a long path.</span></span> <span data-ttu-id="d164e-238">如果您打算將一系列備份寫入相同的路徑名稱或磁帶裝置，使用邏輯備份裝置會很有用。</span><span class="sxs-lookup"><span data-stu-id="d164e-238">Using a logical backup device can help if you plan to write a series of backups to the same path or to a tape device.</span></span> <span data-ttu-id="d164e-239">邏輯備份裝置對於識別磁帶備份裝置特別有用。</span><span class="sxs-lookup"><span data-stu-id="d164e-239">Logical backup devices are especially useful for identifying tape backup devices.</span></span>  
  
 <span data-ttu-id="d164e-240">您可以撰寫備份指令碼來使用特定的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-240">A backup script can be written to use a particular logical backup device.</span></span> <span data-ttu-id="d164e-241">這樣您就可以不更新指令碼而切換到新的實體備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-241">This lets you switch to a new physical backup devices without updating the script.</span></span> <span data-ttu-id="d164e-242">切換時會涉及下列程序：</span><span class="sxs-lookup"><span data-stu-id="d164e-242">Switching involves the following process:</span></span>  
  
1.  <span data-ttu-id="d164e-243">卸除原始邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-243">Dropping the original logical backup device.</span></span>  
  
2.  <span data-ttu-id="d164e-244">定義使用原始邏輯裝置名稱，但對應至不同實體備份裝置的新邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d164e-244">Defining a new logical backup device that uses the original logical device name but maps to a different physical backup device.</span></span> <span data-ttu-id="d164e-245">邏輯備份裝置對於識別磁帶備份裝置特別有用。</span><span class="sxs-lookup"><span data-stu-id="d164e-245">Logical backup devices are especially useful for identifying tape backup devices.</span></span>  
  
##  <a name="mirrored-backup-media-sets"></a><a name="MirroredMediaSets"></a><span data-ttu-id="d164e-246">鏡像備份媒體集</span><span class="sxs-lookup"><span data-stu-id="d164e-246">Mirrored Backup Media Sets</span></span>  
 <span data-ttu-id="d164e-247">備份媒體集的鏡像功能可減少備份裝置功能異常時的影響。</span><span class="sxs-lookup"><span data-stu-id="d164e-247">Mirroring of backup media sets reduces the effect of backup-device malfunctions.</span></span> <span data-ttu-id="d164e-248">這些功能異常會特別嚴重，因為備份是避免資料遺失的最後一道防線。</span><span class="sxs-lookup"><span data-stu-id="d164e-248">These malfunctions are especially serious because backups are the last line of defense against data loss.</span></span> <span data-ttu-id="d164e-249">隨著資料庫大小的成長，備份裝置或媒體故障而導致備份無法還原的可能性也越大。</span><span class="sxs-lookup"><span data-stu-id="d164e-249">As the sizes of databases grow, the probability increases that a failure of a backup device or media will make a backup nonrestorable.</span></span> <span data-ttu-id="d164e-250">鏡像備份媒體可透過提供實體備份裝置的備援性，藉以提升備份的可靠性。</span><span class="sxs-lookup"><span data-stu-id="d164e-250">Mirroring backup media increases the reliability of backups by providing redundancy for the physical backup device.</span></span> <span data-ttu-id="d164e-251">如需詳細資訊，請參閱本主題稍後的 [鏡像備份媒體集 &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)的使用者閱讀。</span><span class="sxs-lookup"><span data-stu-id="d164e-251">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d164e-252">只有 [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] 和更新版本才支援鏡像備份媒體集。</span><span class="sxs-lookup"><span data-stu-id="d164e-252">Mirrored backup media sets are supported only in [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] and later versions.</span></span>  
  
##  <a name="archiving-sql-server-backups"></a><a name="Archiving"></a><span data-ttu-id="d164e-253">封存 SQL Server 備份</span><span class="sxs-lookup"><span data-stu-id="d164e-253">Archiving SQL Server Backups</span></span>  
 <span data-ttu-id="d164e-254">建議您使用檔案系統備份公用程式來封存磁碟備份，並將封存保存在異地。</span><span class="sxs-lookup"><span data-stu-id="d164e-254">We recommend that you use a file system backup utility to archive the disk backups and that you store the archives off-site.</span></span> <span data-ttu-id="d164e-255">使用磁碟的優點是，您可以使用網路將封存的備份寫入異地磁碟。</span><span class="sxs-lookup"><span data-stu-id="d164e-255">Using disk has the advantage that you use the network to write the archived backups onto an off-site disk.</span></span> <span data-ttu-id="d164e-256">Azure Blob 儲存體服務可作為異地封存選項。</span><span class="sxs-lookup"><span data-stu-id="d164e-256">The Azure Blob storage service can be used as off-site archival option.</span></span>  <span data-ttu-id="d164e-257">您可以上傳磁碟備份，或是直接將備份寫入 Azure Blob 儲存體服務中。</span><span class="sxs-lookup"><span data-stu-id="d164e-257">You can either upload your disk backups, or directly write the backups to the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="d164e-258">另一種常見的封存方法是將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份寫入本機備份磁碟、將備份封存至磁帶，然後將磁帶存放在異地。</span><span class="sxs-lookup"><span data-stu-id="d164e-258">Another common archiving approach is to write [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups onto a local backup disk, archive them to tape, and then store the tapes off-site.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d164e-259">相關工作</span><span class="sxs-lookup"><span data-stu-id="d164e-259">Related Tasks</span></span>  
 <span data-ttu-id="d164e-260">**指定磁碟裝置 (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="d164e-260">**To specify a disk device (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="d164e-261">指定磁碟或磁帶作為備份目的地 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-261">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 <span data-ttu-id="d164e-262">**指定磁帶裝置 (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="d164e-262">**To specify a tape device (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="d164e-263">指定磁碟或磁帶作為備份目的地 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-263">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 <span data-ttu-id="d164e-264">**定義邏輯備份裝置**</span><span class="sxs-lookup"><span data-stu-id="d164e-264">**To define a logical backup device**</span></span>  
  
-   [<span data-ttu-id="d164e-265">sp_addumpdevice &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-265">sp_addumpdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
-   [<span data-ttu-id="d164e-266">定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-266">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="d164e-267">定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-267">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   <span data-ttu-id="d164e-268"><xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)</span><span class="sxs-lookup"><span data-stu-id="d164e-268"><xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)</span></span>  
  
 <span data-ttu-id="d164e-269">**使用邏輯備份裝置**</span><span class="sxs-lookup"><span data-stu-id="d164e-269">**To use a logical backup device**</span></span>  
  
-   [<span data-ttu-id="d164e-270">指定磁碟或磁帶作為備份目的地 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-270">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="d164e-271">從裝置還原備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-271">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
-   [<span data-ttu-id="d164e-272">BACKUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-272">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  
-   [<span data-ttu-id="d164e-273">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-273">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
 <span data-ttu-id="d164e-274">**檢視有關備份裝置的資訊**</span><span class="sxs-lookup"><span data-stu-id="d164e-274">**To View Information About Backup Devices**</span></span>  
  
-   [<span data-ttu-id="d164e-275">備份記錄與標頭資訊 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-275">Backup History and Header Information &#40;SQL Server&#41;</span></span>](backup-history-and-header-information-sql-server.md)  
  
-   [<span data-ttu-id="d164e-276">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-276">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="d164e-277">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-277">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
 <span data-ttu-id="d164e-278">**若要刪除邏輯備份裝置**</span><span class="sxs-lookup"><span data-stu-id="d164e-278">**To delete a logical backup device**</span></span>  
  
-   [<span data-ttu-id="d164e-279">sp_dropdevice &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-279">sp_dropdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)  
  
-   [<span data-ttu-id="d164e-280">刪除備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-280">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="d164e-281">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d164e-281">See Also</span></span>  
 <span data-ttu-id="d164e-282">[SQL Server 的 Backup Device 物件](../performance-monitor/sql-server-backup-device-object.md) </span><span class="sxs-lookup"><span data-stu-id="d164e-282">[SQL Server, Backup Device Object](../performance-monitor/sql-server-backup-device-object.md) </span></span>  
 <span data-ttu-id="d164e-283">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d164e-283">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="d164e-284">[維護計畫](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="d164e-284">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 <span data-ttu-id="d164e-285">[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d164e-285">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="d164e-286">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d164e-286">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="d164e-287">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d164e-287">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="d164e-288">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d164e-288">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="d164e-289">[sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d164e-289">[sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) </span></span>  
 [<span data-ttu-id="d164e-290">鏡像備份媒體集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d164e-290">Mirrored Backup Media Sets &#40;SQL Server&#41;</span></span>](mirrored-backup-media-sets-sql-server.md)  
  
  
