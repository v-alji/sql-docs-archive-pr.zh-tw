---
title: 使用備份與還原複製資料庫 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], back up and restore
- restoring databases [SQL Server], previous SQL Server versions
- database restores [SQL Server], copying databases
- restoring databases [SQL Server], onto another server instance
- restoring [SQL Server], onto another server instance
- backing up databases [SQL Server], copying databases
- database backups [SQL Server], copying databases
ms.assetid: b93e9701-72a0-408e-958c-dc196872c040
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8ffed36767f961f7482aa0dccf755118c80c019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699763"
---
# <a name="copy-databases-with-backup-and-restore"></a><span data-ttu-id="90f92-102">使用備份與還原複製資料庫</span><span class="sxs-lookup"><span data-stu-id="90f92-102">Copy Databases with Backup and Restore</span></span>
  <span data-ttu-id="90f92-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，您可以藉由還原使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本所建立的使用者資料庫備份，建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="90f92-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create a new database by restoring a backup of a user database created by using [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version.</span></span> <span data-ttu-id="90f92-104">但是， **無法還原使用舊版**所建立的 **master** 、 **model** 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]備份。</span><span class="sxs-lookup"><span data-stu-id="90f92-104">However, backups of **master**, **model** and **msdb** that were created by using an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="90f92-105">此外，任何舊版 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 都無法還原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]備份。</span><span class="sxs-lookup"><span data-stu-id="90f92-105">Also, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] backups cannot be restored by any earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="90f92-106">使用與之前版本不同的預設路徑。</span><span class="sxs-lookup"><span data-stu-id="90f92-106">uses a different default path than earlier versions.</span></span> <span data-ttu-id="90f92-107">因此，若要還原舊版預設位置中建立的資料庫備份，您就必須使用 MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="90f92-107">Therefore, to restore backups of a database created in the default location of earlier versions you must use the MOVE option.</span></span> <span data-ttu-id="90f92-108">如需有關新預設路徑的詳細資訊，請參閱 [SQL Server 的預設和具名執行個體的檔案位置](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="90f92-108">For information about the new default path see [File Locations for Default and Named Instances of SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).</span></span> <span data-ttu-id="90f92-109">如需移動資料庫檔案的詳細資訊，請參閱本主題稍後的「移動資料庫檔案」。</span><span class="sxs-lookup"><span data-stu-id="90f92-109">For more information about moving database files, see "Moving the Database Files," later in this topic.</span></span>  
  
## <a name="general-steps-for-using-backup-and-restore-to-copy-a-database"></a><span data-ttu-id="90f92-110">使用備份與還原來複製資料庫的一般步驟</span><span class="sxs-lookup"><span data-stu-id="90f92-110">General Steps for Using Backup and Restore to Copy a Database</span></span>  
 <span data-ttu-id="90f92-111">當您使用備份與還原將資料庫複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的另一個執行個體時，來源和目的地電腦可為執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的任何平台。</span><span class="sxs-lookup"><span data-stu-id="90f92-111">When you use backup and restore to copy a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the source and destination computers can be any platform on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs.</span></span>  
  
 <span data-ttu-id="90f92-112">一般步驟如下：</span><span class="sxs-lookup"><span data-stu-id="90f92-112">The general steps are:</span></span>  
  
1.  <span data-ttu-id="90f92-113">備份來源資料庫，它可能在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="90f92-113">Back up the source database, which can reside on an instance of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later.</span></span> <span data-ttu-id="90f92-114">執行這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的電腦稱為 *來源電腦*。</span><span class="sxs-lookup"><span data-stu-id="90f92-114">The computer on which this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running is the *source computer*.</span></span>  
  
2.  <span data-ttu-id="90f92-115">在您要將資料庫複製 (*目的地電腦*的電腦上) ，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 您打算還原資料庫的實例。</span><span class="sxs-lookup"><span data-stu-id="90f92-115">On the computer to which you want to copy the database (the *destination computer*), connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you plan to restore the database.</span></span> <span data-ttu-id="90f92-116">如有需要，請在目的地伺服器執行個體上建立與來源資料庫備份所用的相同備份裝置。</span><span class="sxs-lookup"><span data-stu-id="90f92-116">If needed, on the destination server instance, create the same backup devices as used to the backup of the source databases.</span></span>  
  
3.  <span data-ttu-id="90f92-117">在目的地電腦上還原來源資料庫的備份。</span><span class="sxs-lookup"><span data-stu-id="90f92-117">Restore the backup of the source database on the destination computer.</span></span> <span data-ttu-id="90f92-118">還原資料庫會自動建立所有的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="90f92-118">Restoring the database automatically creates all of the database files.</span></span>  
  
 <span data-ttu-id="90f92-119">下列主題討論會影響此處理序的其他注意事項。</span><span class="sxs-lookup"><span data-stu-id="90f92-119">The following topics address additional considerations that may affect this process.</span></span>  
  
## <a name="before-you-restore-database-files"></a><span data-ttu-id="90f92-120">在還原資料庫檔案之前</span><span class="sxs-lookup"><span data-stu-id="90f92-120">Before You Restore Database Files</span></span>  
 <span data-ttu-id="90f92-121">還原資料庫會自動建立還原資料庫所需的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="90f92-121">Restoring a database automatically creates the database files that are needed by the restoring database.</span></span> <span data-ttu-id="90f92-122">依預設，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在還原處理期間所建立的檔案會使用與來源電腦上的原始資料庫中的備份檔案相同的名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="90f92-122">By default, the files that are created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] during the restoration process use the same names and paths as the backup files from the original database on the source computer.</span></span>  
  
 <span data-ttu-id="90f92-123">(選擇性) 在還原資料庫時，您可以指定還原資料庫的裝置對應、檔案名稱或路徑。</span><span class="sxs-lookup"><span data-stu-id="90f92-123">Optionally, when restoring the database, you can specify the device mapping, file names, or path for the restoring database.</span></span> <span data-ttu-id="90f92-124">在下列狀況中，這可能是必要的步驟：</span><span class="sxs-lookup"><span data-stu-id="90f92-124">This might be necessary in the following situations:</span></span>  
  
-   <span data-ttu-id="90f92-125">原始電腦之資料庫所使用的目錄結構或磁碟機對應不存在其他電腦上。</span><span class="sxs-lookup"><span data-stu-id="90f92-125">The directory structure or drive mapping used by the database on the original computer not exist on the other computer.</span></span> <span data-ttu-id="90f92-126">例如，備份可能包含預設還原至 E 磁碟機的檔案，但目的地電腦沒有 E 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="90f92-126">For example, perhaps the backup contains a file that would be restored to drive E by default, but the destination computer lacks a drive E.</span></span>  
  
-   <span data-ttu-id="90f92-127">目標位置可能空間不夠。</span><span class="sxs-lookup"><span data-stu-id="90f92-127">The target location might have insufficient space.</span></span>  
  
-   <span data-ttu-id="90f92-128">您要重複使用存在還原目的地上的資料庫名稱，而且其任何檔案的名稱都與備份組中的資料庫檔案名稱相同，此時將發生下列其中一種情況：</span><span class="sxs-lookup"><span data-stu-id="90f92-128">You are reusing a database name that exists on the restore destination and any of its files is named the same as a database file in the backup set, one of the following occurs:</span></span>  
  
    -   <span data-ttu-id="90f92-129">如果可覆寫現有的資料庫檔案，系統就會覆寫此檔案 (這就不會影響屬於不同資料庫名稱的檔案)。</span><span class="sxs-lookup"><span data-stu-id="90f92-129">If the existing database file can be overwritten, it will be overwritten (this would not affect a file that belongs to a different database name).</span></span>  
  
    -   <span data-ttu-id="90f92-130">如果無法覆寫現有的檔案，就會發生還原錯誤。</span><span class="sxs-lookup"><span data-stu-id="90f92-130">If the existing file cannot be overwritten, a restore error would occur.</span></span>  
  
 <span data-ttu-id="90f92-131">為了避免錯誤和非預期的結果，在還原作業之前，您可以使用[backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql)歷程記錄資料表，在您計畫還原的備份中找出資料庫和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="90f92-131">To avoid errors and unintended consequences, before the restore operation, you can use the [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql) history table to find out the database and log files in the backup you plan to restore.</span></span>  
  
## <a name="moving-the-database-files"></a><span data-ttu-id="90f92-132">移動資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="90f92-132">Moving the Database Files</span></span>  
 <span data-ttu-id="90f92-133">如果資料庫備份內的檔案因為前述理由而無法還原至目的地電腦，則在還原檔案時必須將檔案移到新位置。</span><span class="sxs-lookup"><span data-stu-id="90f92-133">If the files within the database backup cannot be restored onto the destination computer because of the reasons mentioned earlier, it is necessary to move the files to a new location while they are being restored.</span></span> <span data-ttu-id="90f92-134">例如：</span><span class="sxs-lookup"><span data-stu-id="90f92-134">For example:</span></span>  
  
-   <span data-ttu-id="90f92-135">您想要從建立於舊版預設位置的備份中還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="90f92-135">You want to restore a database from backups created in the default location of the earlier version.</span></span>  
  
-   <span data-ttu-id="90f92-136">由於容量的因素，可能有必要將備份中的部分資料庫檔案還原至其他磁碟機。</span><span class="sxs-lookup"><span data-stu-id="90f92-136">It may be necessary to restore some of the database files in the backup to a different drive because of capacity considerations.</span></span> <span data-ttu-id="90f92-137">這種情況很可能會發生，因為組織內的大部分電腦不會擁有個數與大小一樣的磁碟機，以及完全一樣的軟體組態。</span><span class="sxs-lookup"><span data-stu-id="90f92-137">This is likely to be a common occurrence because most computers within an organization do not have the same number and size of disk drives or identical software configurations.</span></span>  
  
-   <span data-ttu-id="90f92-138">可能有必要在同一部電腦上建立現有資料庫的副本，以供測試之用。</span><span class="sxs-lookup"><span data-stu-id="90f92-138">It may be necessary to create a copy of an existing database on the same computer for testing purposes.</span></span> <span data-ttu-id="90f92-139">在這種情況下，原始資料庫的資料庫檔已存在，所以在還原過程中建立資料庫副本時必須指定不同的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="90f92-139">In this case, the database files for the original database already exist, so different file names need to be specified when the database copy is created during the restore operation.</span></span>  
  
 <span data-ttu-id="90f92-140">如需詳細資訊，請參閱本主題稍後的「將檔案與檔案群組還原至新的位置」。</span><span class="sxs-lookup"><span data-stu-id="90f92-140">For more information, see "To restore files and filegroups to a new location," later in this topic.</span></span>  
  
## <a name="changing-the-database-name"></a><span data-ttu-id="90f92-141">變更資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="90f92-141">Changing the Database Name</span></span>  
 <span data-ttu-id="90f92-142">將資料庫還原至目的電腦時可以變更資料庫的名稱，而不必先還原資料庫，然後手動變更名稱。</span><span class="sxs-lookup"><span data-stu-id="90f92-142">The name of the database can be changed as it is restored to the destination computer, without having to restore the database first and then change the name manually.</span></span> <span data-ttu-id="90f92-143">例如，可能必須將資料庫名稱從 **Sales** 改成 **SalesCopy** ，以指出這是資料庫的副本。</span><span class="sxs-lookup"><span data-stu-id="90f92-143">For example, it may be necessary to change the database name from **Sales** to **SalesCopy** to indicate that this is a copy of a database.</span></span>  
  
 <span data-ttu-id="90f92-144">會自動使用您還原資料庫時明確提供的資料庫名稱做為新的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="90f92-144">The database name that is explicitly supplied when you restore a database is used automatically as the new database name.</span></span> <span data-ttu-id="90f92-145">因為資料庫名稱尚未存在，所以會使用備份中的檔案建立新名稱。</span><span class="sxs-lookup"><span data-stu-id="90f92-145">Because the database name does not already exist, a new one is created by using the files in the backup.</span></span>  
  
## <a name="when-upgrading-a-database-by-using-restore"></a><span data-ttu-id="90f92-146">使用還原來升級資料庫時</span><span class="sxs-lookup"><span data-stu-id="90f92-146">When Upgrading a Database by Using Restore</span></span>  
 <span data-ttu-id="90f92-147">從舊版還原備份時，事先知道備份中的每個全文檢索目錄路徑 (磁碟機和目錄) 是否存在於目的地電腦上會很有協助。</span><span class="sxs-lookup"><span data-stu-id="90f92-147">When restoring backups from an earlier version, it is helpful to know in advance whether the path (drive and directory) of each of the full-text catalogs in a backup exists on the destination computer.</span></span> <span data-ttu-id="90f92-148">若要列出備份中每個檔案 (包括目錄檔案) 的邏輯名稱和實體名稱 (路徑和檔案名稱)，請使用 RESTORE FILELISTONLY FROM *<備份裝置>* 陳述式。</span><span class="sxs-lookup"><span data-stu-id="90f92-148">To list the logical names and physical names, path and file name) of every file in a backup, including the catalog files, use a RESTORE FILELISTONLY FROM *<backup_device>* statement.</span></span> <span data-ttu-id="90f92-149">如需詳細資訊，請參閱 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="90f92-149">For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>  
  
 <span data-ttu-id="90f92-150">如果目的地電腦上並無相同路徑存在，則您有兩個替代方案：</span><span class="sxs-lookup"><span data-stu-id="90f92-150">If the same path does not exist on the destination computer, you have two alternatives:</span></span>  
  
-   <span data-ttu-id="90f92-151">在目的地電腦上建立同等的磁碟機/目錄對應。</span><span class="sxs-lookup"><span data-stu-id="90f92-151">Create the equivalent drive/directory mapping on the destination computer.</span></span>  
  
-   <span data-ttu-id="90f92-152">在還原作業期間，在 RESTORE DATABASE 陳述式中使用 WITH MOVE 子句，將目錄檔案移到新位置。</span><span class="sxs-lookup"><span data-stu-id="90f92-152">Move the catalog files to a new location during the restore operation, by using the WITH MOVE clause in your RESTORE DATABASE statement.</span></span> <span data-ttu-id="90f92-153">如需詳細資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)備份。</span><span class="sxs-lookup"><span data-stu-id="90f92-153">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
 <span data-ttu-id="90f92-154">如需升級全文檢索索引之替代選項的相關資訊，請參閱 [升級全文檢索搜尋](../search/upgrade-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="90f92-154">For information about alternative options for upgrading full-text indexes, see [Upgrade Full-Text Search](../search/upgrade-full-text-search.md).</span></span>  
  
## <a name="database-ownership"></a><span data-ttu-id="90f92-155">資料庫擁有權</span><span class="sxs-lookup"><span data-stu-id="90f92-155">Database Ownership</span></span>  
 <span data-ttu-id="90f92-156">當資料庫在另一部電腦上還原時，初始還原作業的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 使用者會自動變成新資料庫的擁有者。</span><span class="sxs-lookup"><span data-stu-id="90f92-156">When a database is restored on another computer, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user who initiates the restore operation becomes the owner of the new database automatically.</span></span> <span data-ttu-id="90f92-157">還原資料庫時，系統管理員或新的資料庫擁有者可以變更資料庫擁有權。</span><span class="sxs-lookup"><span data-stu-id="90f92-157">When the database is restored, the system administrator or the new database owner can change database ownership.</span></span> <span data-ttu-id="90f92-158">若要防止未經授權的資料庫還原，請使用媒體或備份組密碼。</span><span class="sxs-lookup"><span data-stu-id="90f92-158">To prevent unauthorized restoration of a database, use media or backup set passwords.</span></span>  
  
## <a name="managing-metadata-when-restoring-to-another-server-instance"></a><span data-ttu-id="90f92-159">還原至另一個伺服器執行個體時管理中繼資料</span><span class="sxs-lookup"><span data-stu-id="90f92-159">Managing Metadata When Restoring to Another Server Instance</span></span>  
 <span data-ttu-id="90f92-160">當您在另一個伺服器執行個體還原資料庫時，為了提供一致的經驗給使用者和應用程式，您可能需要在其他伺服器執行個體上為資料庫重新建立部分或全部的中繼資料，例如登入和作業。</span><span class="sxs-lookup"><span data-stu-id="90f92-160">When you restore a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="90f92-161">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="90f92-161">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
 <span data-ttu-id="90f92-162">**檢視備份組中的資料與記錄檔**</span><span class="sxs-lookup"><span data-stu-id="90f92-162">**To view the data and log files in a backup set**</span></span>  
  
-   [<span data-ttu-id="90f92-163">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90f92-163">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
 <span data-ttu-id="90f92-164">**將檔案與檔案群組還原至新的位置**</span><span class="sxs-lookup"><span data-stu-id="90f92-164">**To restore files and filegroups to a new location**</span></span>  
  
-   [<span data-ttu-id="90f92-165">將檔案還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90f92-165">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="90f92-166">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="90f92-166">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 <span data-ttu-id="90f92-167">**若要以覆蓋現有檔案的方式還原檔案與檔案群組**</span><span class="sxs-lookup"><span data-stu-id="90f92-167">**To restore files and filegroups over existing files**</span></span>  
  
-   [<span data-ttu-id="90f92-168">以覆蓋現有檔案的方式還原檔案與檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="90f92-168">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
 <span data-ttu-id="90f92-169">**若要使用新名稱還原資料庫**</span><span class="sxs-lookup"><span data-stu-id="90f92-169">**To restore a database with a new name**</span></span>  
  
-   [<span data-ttu-id="90f92-170">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="90f92-170">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 <span data-ttu-id="90f92-171">**若要重新啟動被中斷的還原作業**</span><span class="sxs-lookup"><span data-stu-id="90f92-171">**To restart an interrupted restore operation**</span></span>  
  
-   [<span data-ttu-id="90f92-172">重新啟動中斷的還原作業 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90f92-172">Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;</span></span>](../backup-restore/restart-an-interrupted-restore-operation-transact-sql.md)  
  
 <span data-ttu-id="90f92-173">**變更資料庫的擁有者**</span><span class="sxs-lookup"><span data-stu-id="90f92-173">**To change the owner of a database**</span></span>  
  
-   [<span data-ttu-id="90f92-174">sp_changedbowner &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90f92-174">sp_changedbowner &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-changedbowner-transact-sql)  
  
 <span data-ttu-id="90f92-175">**使用 SQL Server 管理物件 (SMO) 複製資料庫**</span><span class="sxs-lookup"><span data-stu-id="90f92-175">**To copy a database by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.RelocateFiles%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReplaceDatabase%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
## <a name="see-also"></a><span data-ttu-id="90f92-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90f92-176">See Also</span></span>  
 <span data-ttu-id="90f92-177">[複製資料庫至其他伺服器](copy-databases-to-other-servers.md) </span><span class="sxs-lookup"><span data-stu-id="90f92-177">[Copy Databases to Other Servers](copy-databases-to-other-servers.md) </span></span>  
 <span data-ttu-id="90f92-178">[SQL Server 的預設和具名執行個體的檔案位置](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="90f92-178">[File Locations for Default and Named Instances of SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="90f92-179">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90f92-179">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 [<span data-ttu-id="90f92-180">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90f92-180">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
