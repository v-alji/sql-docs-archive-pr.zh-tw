---
title: 移動使用者資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- editions [SQL Server], moving databases between
- moving full-text catalogs
- scheduled disk maintenace [SQL Server]
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- moving user databases
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: ad9a4e92-13fb-457d-996a-66ffc2d55b79
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6c2b82c3bec13c82aa30aebd175ef78f8136ee04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595101"
---
# <a name="move-user-databases"></a><span data-ttu-id="7531d-102">移動使用者資料庫</span><span class="sxs-lookup"><span data-stu-id="7531d-102">Move User Databases</span></span>
  <span data-ttu-id="7531d-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，您可以在 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 陳述式的 FILENAME 子句中指定新的檔案位置，以便將使用者資料庫的資料、記錄和全文檢索目錄檔案移到新位置。</span><span class="sxs-lookup"><span data-stu-id="7531d-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can move the data, log, and full-text catalog files of a user database to a new location by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="7531d-104">這種方法適用於在相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體內移動資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="7531d-104">This method applies to moving database files within the same instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7531d-105">若要將資料庫移到另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體或移到另一個伺服器，請使用 [備份和還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) 或 [卸離和附加作業](move-a-database-using-detach-and-attach-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="7531d-105">To move a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to another server, use [backup and restore](../backup-restore/back-up-and-restore-of-sql-server-databases.md) or [detach and attach operations](move-a-database-using-detach-and-attach-transact-sql.md).</span></span>  
  
## <a name="considerations"></a><span data-ttu-id="7531d-106">考量</span><span class="sxs-lookup"><span data-stu-id="7531d-106">Considerations</span></span>  
 <span data-ttu-id="7531d-107">將資料庫移動到其他伺服器執行個體，以提供一致的經驗給使用者和應用程式時，您可能必須為資料庫重新建立部分或全部的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7531d-107">When you move a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all the metadata for the database.</span></span> <span data-ttu-id="7531d-108">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7531d-108">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
 <span data-ttu-id="7531d-109">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的某些功能會變更 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 將資訊儲存在資料庫檔案中的方式，</span><span class="sxs-lookup"><span data-stu-id="7531d-109">Some features of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] change the way that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores information in the database files.</span></span> <span data-ttu-id="7531d-110">這些功能受限為特定版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7531d-110">These features are restricted to specific editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7531d-111">包含這些功能的資料庫無法移至不支援它們的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="7531d-111">A database that contains these features cannot be moved to an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that does not support them.</span></span> <span data-ttu-id="7531d-112">您可以使用 sys.dm_db_persisted_sku_features 動態管理檢視來列出目前資料庫中啟用的所有版本特有功能。</span><span class="sxs-lookup"><span data-stu-id="7531d-112">Use the sys.dm_db_persisted_sku_features dynamic management view to list all edition-specific features that are enabled in the current database.</span></span>  
  
 <span data-ttu-id="7531d-113">本主題中的程序需要資料庫檔案的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="7531d-113">The procedures in this topic require the logical name of the database files.</span></span> <span data-ttu-id="7531d-114">若要取得該名稱，請查詢 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 目錄檢視中的 name 資料行。</span><span class="sxs-lookup"><span data-stu-id="7531d-114">To obtain the name, query the name column in the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="7531d-115">從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]開始，全文檢索目錄會整合到儲存於檔案系統中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="7531d-115">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], full-text catalogs are integrated into the database rather than being stored in the file system.</span></span> <span data-ttu-id="7531d-116">現在當您移動資料庫時，全文檢索目錄會自動移動。</span><span class="sxs-lookup"><span data-stu-id="7531d-116">The full-text catalogs now move automatically when you move a database.</span></span>  
  
## <a name="planned-relocation-procedure"></a><span data-ttu-id="7531d-117">計畫的重新放置程序</span><span class="sxs-lookup"><span data-stu-id="7531d-117">Planned Relocation Procedure</span></span>  
 <span data-ttu-id="7531d-118">若要依照計畫的重新放置來移動資料或記錄檔，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7531d-118">To move a data or log file as part of a planned relocation, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7531d-119">執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="7531d-119">Run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name SET OFFLINE;  
    ```  
  
2.  <span data-ttu-id="7531d-120">將一個或多個檔案移到新位置。</span><span class="sxs-lookup"><span data-stu-id="7531d-120">Move the file or files to the new location.</span></span>  
  
3.  <span data-ttu-id="7531d-121">對於移動的每個檔案，執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="7531d-121">For each file moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name, FILENAME = 'new_path\os_file_name' );  
    ```  
  
4.  <span data-ttu-id="7531d-122">執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="7531d-122">Run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name SET ONLINE;  
    ```  
  
5.  <span data-ttu-id="7531d-123">執行下列查詢以驗證檔案變更。</span><span class="sxs-lookup"><span data-stu-id="7531d-123">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="relocation-for-scheduled-disk-maintenance"></a><span data-ttu-id="7531d-124">排程的磁碟維謢重新放置</span><span class="sxs-lookup"><span data-stu-id="7531d-124">Relocation for Scheduled Disk Maintenance</span></span>  
 <span data-ttu-id="7531d-125">若要在排程的磁碟維護程序中重新放置檔案，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7531d-125">To relocate a file as part of a scheduled disk maintenance process, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7531d-126">對於要移動的每個檔案執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="7531d-126">For each file to be moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
2.  <span data-ttu-id="7531d-127">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體或關閉系統以執行維護。</span><span class="sxs-lookup"><span data-stu-id="7531d-127">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or shut down the system to perform maintenance.</span></span> <span data-ttu-id="7531d-128">如需詳細資訊，請參閱 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7531d-128">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="7531d-129">將一個或多個檔案移到新位置。</span><span class="sxs-lookup"><span data-stu-id="7531d-129">Move the file or files to the new location.</span></span>  
  
4.  <span data-ttu-id="7531d-130">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體或伺服器。</span><span class="sxs-lookup"><span data-stu-id="7531d-130">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the server.</span></span> <span data-ttu-id="7531d-131">如需詳細資訊，請參閱 [啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7531d-131">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)</span></span>  
  
5.  <span data-ttu-id="7531d-132">執行下列查詢以驗證檔案變更。</span><span class="sxs-lookup"><span data-stu-id="7531d-132">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="failure-recovery-procedure"></a><span data-ttu-id="7531d-133">失敗復原程序</span><span class="sxs-lookup"><span data-stu-id="7531d-133">Failure Recovery Procedure</span></span>  
 <span data-ttu-id="7531d-134">如果因為硬體失敗必須移動檔案，請遵循下列步驟將檔案重新放置到新位置。</span><span class="sxs-lookup"><span data-stu-id="7531d-134">If a file must be moved because of a hardware failure, use the following steps to relocate the file to a new location.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7531d-135">如果無法啟動資料庫，也就是資料庫在質疑模式下或在無法復原的狀態下，只有 sysadmin 固定角色的成員可以移動檔案。</span><span class="sxs-lookup"><span data-stu-id="7531d-135">If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.</span></span>  
  
1.  <span data-ttu-id="7531d-136">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體已經啟動，請將它停止。</span><span class="sxs-lookup"><span data-stu-id="7531d-136">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if it is started.</span></span>  
  
2.  <span data-ttu-id="7531d-137">在命令提示字元下輸入下列其中一個命令，以僅限 master 的復原模式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7531d-137">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in master-only recovery mode by entering one of the following commands at the command prompt.</span></span>  
  
    -   <span data-ttu-id="7531d-138">如果是預設 (MSSQLSERVER) 執行個體，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="7531d-138">For the default (MSSQLSERVER) instance, run the following command.</span></span>  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   <span data-ttu-id="7531d-139">如果是具名執行個體，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="7531d-139">For a named instance, run the following command.</span></span>  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     <span data-ttu-id="7531d-140">如需詳細資訊，請參閱 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7531d-140">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="7531d-141">對於要移動的每個檔案，使用 **sqlcmd** 命令或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 來執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="7531d-141">For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
     <span data-ttu-id="7531d-142">如需如何使用 **sqlcmd** 公用程式的詳細資訊，請參閱 [使用 sqlcmd 公用程式](../scripting/sqlcmd-use-the-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="7531d-142">For more information about how to use the **sqlcmd** utility, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
4.  <span data-ttu-id="7531d-143">結束 **sqlcmd** 公用程式或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7531d-143">Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
5.  <span data-ttu-id="7531d-144">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7531d-144">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
6.  <span data-ttu-id="7531d-145">將一個或多個檔案移到新位置。</span><span class="sxs-lookup"><span data-stu-id="7531d-145">Move the file or files to the new location.</span></span>  
  
7.  <span data-ttu-id="7531d-146">啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="7531d-146">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7531d-147">例如，請執行： `NET START MSSQLSERVER`。</span><span class="sxs-lookup"><span data-stu-id="7531d-147">For example, run: `NET START MSSQLSERVER`.</span></span>  
  
8.  <span data-ttu-id="7531d-148">執行下列查詢以驗證檔案變更。</span><span class="sxs-lookup"><span data-stu-id="7531d-148">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="examples"></a><span data-ttu-id="7531d-149">範例</span><span class="sxs-lookup"><span data-stu-id="7531d-149">Examples</span></span>  
 <span data-ttu-id="7531d-150">下列範例會以計畫的重新放置，將 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 記錄檔移到新位置。</span><span class="sxs-lookup"><span data-stu-id="7531d-150">The following example moves the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] log file to a new location as part of a planned relocation.</span></span>  
  
```  
USE master;  
GO  
-- Return the logical file name.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
GO  
ALTER DATABASE AdventureWorks2012 SET OFFLINE;  
GO  
-- Physically move the file to a new location.  
-- In the following statement, modify the path specified in FILENAME to  
-- the new location of the file on your server.  
ALTER DATABASE AdventureWorks2012   
    MODIFY FILE ( NAME = AdventureWorks2012_Log,   
                  FILENAME = 'C:\NewLoc\AdventureWorks2012_Log.ldf');  
GO  
ALTER DATABASE AdventureWorks2012 SET ONLINE;  
GO  
--Verify the new location.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
```  
  
## <a name="see-also"></a><span data-ttu-id="7531d-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7531d-151">See Also</span></span>  
 <span data-ttu-id="7531d-152">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7531d-152">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="7531d-153">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7531d-153">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="7531d-154">[資料庫卸離和附加 &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7531d-154">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="7531d-155">[移動系統資料庫](system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="7531d-155">[Move System Databases](system-databases.md) </span></span>  
 <span data-ttu-id="7531d-156">[移動資料庫檔案](move-database-files.md) </span><span class="sxs-lookup"><span data-stu-id="7531d-156">[Move Database Files](move-database-files.md) </span></span>  
 <span data-ttu-id="7531d-157">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7531d-157">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="7531d-158">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7531d-158">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="7531d-159">啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="7531d-159">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
