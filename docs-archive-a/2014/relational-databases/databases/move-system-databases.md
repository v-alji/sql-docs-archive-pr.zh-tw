---
title: 移動系統資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- moving system databases
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- tempdb database [SQL Server], moving
- system databases [SQL Server], moving
- scheduled disk maintenace [SQL Server]
- moving databases
- msdb database [SQL Server], moving
- moving database files
- relocating database files
- planned database relocations [SQL Server]
- master database [SQL Server], moving
- model database [SQL Server], moving
- Resource database [SQL Server]
- databases [SQL Server], moving
ms.assetid: 72bb62ee-9602-4f71-be51-c466c1670878
author: stevestein
ms.author: sstein
ms.openlocfilehash: 748d781d6bbefb0dc710427a34ebd71ec7037fdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710689"
---
# <a name="move-system-databases"></a><span data-ttu-id="7b0fb-102">移動系統資料庫</span><span class="sxs-lookup"><span data-stu-id="7b0fb-102">Move System Databases</span></span>
  <span data-ttu-id="7b0fb-103">本主題將描述如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中移動系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-103">This topic describes how to move system databases in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b0fb-104">在下列狀況下移動系統資料庫可能非常有用：</span><span class="sxs-lookup"><span data-stu-id="7b0fb-104">Moving system databases may be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="7b0fb-105">失敗復原。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-105">Failure recovery.</span></span> <span data-ttu-id="7b0fb-106">例如，資料庫因硬體失敗而進入質疑模式或被關閉。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-106">For example, the database is in suspect mode or has shut down because of a hardware failure.</span></span>  
  
-   <span data-ttu-id="7b0fb-107">計畫的重新放置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-107">Planned relocation.</span></span>  
  
-   <span data-ttu-id="7b0fb-108">排程的磁碟維護重新放置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-108">Relocation for scheduled disk maintenance.</span></span>  
  
 <span data-ttu-id="7b0fb-109">下列程序適用於在相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體內移動資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-109">The following procedures apply to moving database files within the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b0fb-110">若要將資料庫移到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的另一個執行個體或移到其他伺服器，請使用 [備份和還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) 或 [卸離和附加](move-a-database-using-detach-and-attach-transact-sql.md) 作業。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-110">To move a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to another server, use the [backup and restore](../backup-restore/back-up-and-restore-of-sql-server-databases.md) or [detach and attach](move-a-database-using-detach-and-attach-transact-sql.md) operations.</span></span>  
  
 <span data-ttu-id="7b0fb-111">本主題中的程序需要資料庫檔案的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-111">The procedures in this topic require the logical name of the database files.</span></span> <span data-ttu-id="7b0fb-112">若要取得該名稱，請查詢 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 目錄檢視中的 name 資料行。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-112">To obtain the name, query the name column in the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7b0fb-113">如果您移動了系統資料庫，接著重建 master 資料庫，就必須再次移動系統資料庫，因為重建作業會將所有系統資料庫安裝到預設的位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-113">If you move a system database and later rebuild the master database, you must move the system database again because the rebuild operation installs all system databases to their default location.</span></span>  
  
##  <a name="in-this-topic"></a><a name="Intro"></a> <span data-ttu-id="7b0fb-114">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="7b0fb-114">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="7b0fb-115">規劃的重新配置和排程的磁片維護程式</span><span class="sxs-lookup"><span data-stu-id="7b0fb-115">Planned Relocation and Scheduled Disk Maintenance Procedure</span></span>](#Planned)  
  
-   [<span data-ttu-id="7b0fb-116">失敗修復程式</span><span class="sxs-lookup"><span data-stu-id="7b0fb-116">Failure Recovery Procedure</span></span>](#Failure)  
  
-   [<span data-ttu-id="7b0fb-117">移動 master 資料庫</span><span class="sxs-lookup"><span data-stu-id="7b0fb-117">Moving the master Database</span></span>](#master)  
  
-   [<span data-ttu-id="7b0fb-118">移動 Resource 資料庫</span><span class="sxs-lookup"><span data-stu-id="7b0fb-118">Moving the Resource Database</span></span>](#Resource)  
  
-   [<span data-ttu-id="7b0fb-119">後續操作：移動所有系統資料庫之後</span><span class="sxs-lookup"><span data-stu-id="7b0fb-119">Follow-up: After Moving All System Databases</span></span>](#Follow)  
  
-   [<span data-ttu-id="7b0fb-120">範例</span><span class="sxs-lookup"><span data-stu-id="7b0fb-120">Examples</span></span>](#Examples)  
  
##  <a name="planned-relocation-and-scheduled-disk-maintenance-procedure"></a><a name="Planned"></a> <span data-ttu-id="7b0fb-121">計畫的重新放置與排程的磁碟維謢程序</span><span class="sxs-lookup"><span data-stu-id="7b0fb-121">Planned Relocation and Scheduled Disk Maintenance Procedure</span></span>  
 <span data-ttu-id="7b0fb-122">若要以計畫的重新放置或排程的維護作業來移動系統資料庫資料或記錄檔，請遵照下列步驟執行。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-122">To move a system database data or log file as part of a planned relocation or scheduled maintenance operation, follow these steps.</span></span> <span data-ttu-id="7b0fb-123">此程序適用於 master 和 Resource 資料庫以外的所有系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-123">This procedure applies to all system databases except the master and Resource databases.</span></span>  
  
1.  <span data-ttu-id="7b0fb-124">對於要移動的每個檔案執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-124">For each file to be moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
2.  <span data-ttu-id="7b0fb-125">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體或關閉系統以執行維護。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-125">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or shut down the system to perform maintenance.</span></span> <span data-ttu-id="7b0fb-126">如需詳細資訊，請參閱 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-126">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="7b0fb-127">將一個或多個檔案移到新位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-127">Move the file or files to the new location.</span></span>  
  
4.  <span data-ttu-id="7b0fb-128">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體或伺服器。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-128">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the server.</span></span> <span data-ttu-id="7b0fb-129">如需詳細資訊，請參閱 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-129">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
5.  <span data-ttu-id="7b0fb-130">執行下列查詢以驗證檔案變更。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-130">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
 <span data-ttu-id="7b0fb-131">如果移動 msdb 資料庫，並針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Mail [設定了](../database-mail/database-mail.md)的執行個體，請完成下列額外步驟。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-131">If the msdb database is moved and the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured for [Database Mail](../database-mail/database-mail.md), complete these additional steps.</span></span>  
  
1.  <span data-ttu-id="7b0fb-132">透過執行下列查詢，確認已為 msdb 資料庫啟用 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-132">Verify that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] is enabled for the msdb database by running the following query.</span></span>  
  
    ```  
    SELECT is_broker_enabled   
    FROM sys.databases  
    WHERE name = N'msdb';  
    ```  
  
     <span data-ttu-id="7b0fb-133">如需啟用 [!INCLUDE[ssSB](../../../includes/sssb-md.md)]的詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)中移動系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-133">For more information about enabling [!INCLUDE[ssSB](../../../includes/sssb-md.md)], see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
2.  <span data-ttu-id="7b0fb-134">透過傳送測試郵件，確認 Database Mail 是否可正常運作。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-134">Verify that Database Mail is working by sending a test mail.</span></span>  
  
##  <a name="failure-recovery-procedure"></a><a name="Failure"></a> <span data-ttu-id="7b0fb-135">失敗復原程序</span><span class="sxs-lookup"><span data-stu-id="7b0fb-135">Failure Recovery Procedure</span></span>  
 <span data-ttu-id="7b0fb-136">如果因為硬體失敗必須移動檔案，請遵照下列步驟將檔案重新放置到新位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-136">If a file must be moved because of a hardware failure, follow these steps to relocate the file to a new location.</span></span> <span data-ttu-id="7b0fb-137">此程序適用於 master 和 Resource 資料庫以外的所有系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-137">This procedure applies to all system databases except the master and Resource databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7b0fb-138">如果無法啟動資料庫，也就是資料庫在質疑模式下或在無法復原的狀態下，只有 sysadmin 固定角色的成員可以移動檔案。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-138">If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.</span></span>  
  
1.  <span data-ttu-id="7b0fb-139">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體已經啟動，請將它停止。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-139">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if it is started.</span></span>  
  
2.  <span data-ttu-id="7b0fb-140">在命令提示字元下輸入下列其中一個命令，以僅限 master 的復原模式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-140">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in master-only recovery mode by entering one of the following commands at the command prompt.</span></span> <span data-ttu-id="7b0fb-141">在這些命令中指定的參數要區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-141">The parameters specified in these commands are case sensitive.</span></span> <span data-ttu-id="7b0fb-142">如果未依照所示指定參數，命令將會失敗。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-142">The commands fail when the parameters are not specified as shown.</span></span>  
  
    -   <span data-ttu-id="7b0fb-143">如果是預設 (MSSQLSERVER) 執行個體，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7b0fb-143">For the default (MSSQLSERVER) instance, run the following command:</span></span>  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   <span data-ttu-id="7b0fb-144">如果是具名執行個體，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7b0fb-144">For a named instance, run the following command:</span></span>  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     <span data-ttu-id="7b0fb-145">如需詳細資訊，請參閱 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-145">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="7b0fb-146">對於要移動的每個檔案，使用 **sqlcmd** 命令或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 來執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-146">For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
     <span data-ttu-id="7b0fb-147">如需使用 **sqlcmd** 公用程式的詳細資訊，請參閱 [使用 sqlcmd 公用程式](../scripting/sqlcmd-use-the-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-147">For more information about using the **sqlcmd** utility, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
4.  <span data-ttu-id="7b0fb-148">結束 **sqlcmd** 公用程式或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-148">Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
5.  <span data-ttu-id="7b0fb-149">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-149">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b0fb-150">例如，請執行 `NET STOP MSSQLSERVER`。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-150">For example, run `NET STOP MSSQLSERVER`.</span></span>  
  
6.  <span data-ttu-id="7b0fb-151">將一個或多個檔案移到新位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-151">Move the file or files to the new location.</span></span>  
  
7.  <span data-ttu-id="7b0fb-152">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-152">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b0fb-153">例如，請執行 `NET START MSSQLSERVER`。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-153">For example, run `NET START MSSQLSERVER`.</span></span>  
  
8.  <span data-ttu-id="7b0fb-154">執行下列查詢以驗證檔案變更。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-154">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
##  <a name="moving-the-master-database"></a><a name="master"></a> <span data-ttu-id="7b0fb-155">移動 master 資料庫</span><span class="sxs-lookup"><span data-stu-id="7b0fb-155">Moving the master Database</span></span>  
 <span data-ttu-id="7b0fb-156">若要移動 master 資料庫，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-156">To move the master database, follow these steps.</span></span>  
  
1.  <span data-ttu-id="7b0fb-157">從 **[開始]** 功能表上，依序指向 **[程式集]** 、 **[Microsoft SQL Server]** 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-157">From the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="7b0fb-158">在 **[SQL Server 服務]** 節點中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體 (例如 **[SQL Server (MSSQLSERVER)]** )，然後選擇 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-158">In the **SQL Server Services** node, right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (for example, **SQL Server (MSSQLSERVER)**) and choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="7b0fb-159">在 [ **SQL Server (***Instance_name***) 屬性**] 對話方塊中，按一下 [**啟動參數**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-159">In the **SQL Server (***instance_name***) Properties** dialog box, click the **Startup Parameters** tab.</span></span>  
  
4.  <span data-ttu-id="7b0fb-160">在 [現有參數] 方塊中，選取 -d 參數來移動 master 資料檔案。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-160">In the **Existing parameters** box, select the -d parameter to move the master data file.</span></span> <span data-ttu-id="7b0fb-161">按一下 **[更新]** 來儲存變更。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-161">Click **Update** to save the change.</span></span>  
  
     <span data-ttu-id="7b0fb-162">在 [指定啟動參數] 方塊中，將參數變更為 master 資料庫的新路徑。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-162">In the **Specify a startup parameter** box, change the parameter to the new path of the master database.</span></span>  
  
5.  <span data-ttu-id="7b0fb-163">在 [現有參數] 方塊中，選取 -l 參數來移動 master 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-163">In the **Existing parameters** box, select the -l parameter to move the master log file.</span></span> <span data-ttu-id="7b0fb-164">按一下 **[更新]** 來儲存變更。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-164">Click **Update** to save the change.</span></span>  
  
     <span data-ttu-id="7b0fb-165">在 [指定啟動參數] 方塊中，將參數變更為 master 資料庫的新路徑。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-165">In the **Specify a startup parameter** box, change the parameter to the new path of the master database.</span></span>  
  
     <span data-ttu-id="7b0fb-166">資料檔案的參數值必須遵照 `-d` 參數，而記錄檔的值則必須遵照 `-l` 參數。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-166">The parameter value for the data file must follow the `-d` parameter and the value for the log file must follow the `-l` parameter.</span></span> <span data-ttu-id="7b0fb-167">下列範例顯示 master 資料檔案的預設位置參數值。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-167">The following example shows the parameter values for the default location of the master data file.</span></span>  
  
     `-dC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\master.mdf`  
  
     `-lC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\mastlog.ldf`  
  
     <span data-ttu-id="7b0fb-168">如果 master 資料檔案計畫的重新放置為 `E:\SQLData`，則必須將參數值變更如下：</span><span class="sxs-lookup"><span data-stu-id="7b0fb-168">If the planned relocation for the master data file is `E:\SQLData`, the parameter values would be changed as follows:</span></span>  
  
     `-dE:\SQLData\master.mdf`  
  
     `-lE:\SQLData\mastlog.ldf`  
  
6.  <span data-ttu-id="7b0fb-169">以滑鼠右鍵按一下執行個體名稱並選擇 [停止]，即可停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-169">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by right-clicking the instance name and choosing **Stop**.</span></span>  
  
7.  <span data-ttu-id="7b0fb-170">將 master.mdf 和 mastlog.ldf 檔移至新位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-170">Move the master.mdf and mastlog.ldf files to the new location.</span></span>  
  
8.  <span data-ttu-id="7b0fb-171">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-171">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
9. <span data-ttu-id="7b0fb-172">執行下列查詢，驗證 master 資料庫的檔案變更。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-172">Verify the file change for the master database by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID('master');  
    GO  
    ```  
  
##  <a name="moving-the-resource-database"></a><a name="Resource"></a> <span data-ttu-id="7b0fb-173">移動 Resource 資料庫</span><span class="sxs-lookup"><span data-stu-id="7b0fb-173">Moving the Resource Database</span></span>  
 <span data-ttu-id="7b0fb-174">Resource 資料庫的位置是 \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-174">The location of the Resource database is \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\.</span></span> <span data-ttu-id="7b0fb-175">此資料庫無法移動。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-175">The database cannot be moved.</span></span>  
  
##  <a name="follow-up-after-moving-all-system-databases"></a><a name="Follow"></a> <span data-ttu-id="7b0fb-176">後續操作：移動所有系統資料庫之後</span><span class="sxs-lookup"><span data-stu-id="7b0fb-176">Follow-up: After Moving All System Databases</span></span>  
 <span data-ttu-id="7b0fb-177">如果您將所有系統資料庫移動至新的磁碟機或磁碟區，或是移動至使用不同磁碟機代號的另一部伺服器，請進行下列更新。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-177">If you have moved all of the system databases to a new drive or volume or to another server with a different drive letter, make the following updates.</span></span>  
  
-   <span data-ttu-id="7b0fb-178">變更 SQL Server Agent 記錄路徑。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-178">Change the SQL Server Agent log path.</span></span> <span data-ttu-id="7b0fb-179">如果您未更新此路徑，SQL Server Agent 將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-179">If you do not update this path, SQL Server Agent will fail to start.</span></span>  
  
-   <span data-ttu-id="7b0fb-180">變更資料庫預設位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-180">Change the database default location.</span></span> <span data-ttu-id="7b0fb-181">如果指定為預設位置的磁碟機代號和路徑不存在，則建立新資料庫可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-181">Creating a new database may fail if the drive letter and path specified as the default location do not exist.</span></span>  
  
#### <a name="change-the-sql-server-agent-log-path"></a><span data-ttu-id="7b0fb-182">變更 SQL Server Agent 記錄路徑</span><span class="sxs-lookup"><span data-stu-id="7b0fb-182">Change the SQL Server Agent Log Path</span></span>  
  
1.  <span data-ttu-id="7b0fb-183">從 SQL Server Management Studio，在 [物件總管] 中展開 **[SQL Server Agent]** 。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-183">From SQL Server Management Studio, in Object Explorer, expand **SQL Server Agent**.</span></span>  
  
2.  <span data-ttu-id="7b0fb-184">以滑鼠右鍵按一下 **[錯誤記錄檔]** ，然後按一下 **[設定]** 。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-184">Right-click **Error Logs** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="7b0fb-185">在 **[設定 SQL Server Agent 錯誤記錄檔]** 對話方塊中，指定 SQLAGENT.OUT 檔的新位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-185">In the **Configure SQL Server Agent Error Logs** dialog box, specify the new location of the SQLAGENT.OUT file.</span></span> <span data-ttu-id="7b0fb-186">預設位置為 C:\Program Files\Microsoft SQL Server\MSSQL12. <instance_name> \MSSQL\Log \\ 。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-186">The default location is C:\Program Files\Microsoft SQL Server\MSSQL12.<instance_name>\MSSQL\Log\\.</span></span>  
  
#### <a name="change-the-database-default-location"></a><span data-ttu-id="7b0fb-187">變更資料庫預設位置</span><span class="sxs-lookup"><span data-stu-id="7b0fb-187">Change the database default location</span></span>  
  
1.  <span data-ttu-id="7b0fb-188">從 SQL Server Management Studio，在 [物件總管] 中以滑鼠右鍵按一下 SQL Server 伺服器，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-188">From SQL Server Management Studio, in Object Explorer, right-click the SQL Server server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7b0fb-189">在 **[伺服器屬性]** 對話方塊中，選取 **[資料庫設定]** 。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-189">In the **Server Properties** dialog box, select **Database Settings**.</span></span>  
  
3.  <span data-ttu-id="7b0fb-190">在 **[資料庫預設位置]** 底下，瀏覽至資料和記錄檔的新位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-190">Under **Database Default Locations**, browse to the new location for both the data and log files.</span></span>  
  
4.  <span data-ttu-id="7b0fb-191">停止 SQL Server 服務然後啟動它來完成變更。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-191">Stop and start the SQL Server service to complete the change.</span></span>  
  
##  <a name="examples"></a><a name="Examples"></a> <span data-ttu-id="7b0fb-192">範例</span><span class="sxs-lookup"><span data-stu-id="7b0fb-192">Examples</span></span>  
  
### <a name="a-moving-the-tempdb-database"></a><span data-ttu-id="7b0fb-193">A.</span><span class="sxs-lookup"><span data-stu-id="7b0fb-193">A.</span></span> <span data-ttu-id="7b0fb-194">移動 tempdb 資料庫</span><span class="sxs-lookup"><span data-stu-id="7b0fb-194">Moving the tempdb database</span></span>  
 <span data-ttu-id="7b0fb-195">下列範例會以計畫的重新放置，將 `tempdb` 資料和記錄檔移到新位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-195">The following example moves the `tempdb` data and log files to a new location as part of a planned relocation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b0fb-196">由於在每次啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時都會重新建立 tempdb，因此您不需要實際移動資料和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-196">Because tempdb is re-created each time the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started, you do not have to physically move the data and log files.</span></span> <span data-ttu-id="7b0fb-197">在步驟 3 重新啟動此服務時，將會在新位置建立檔案。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-197">The files are created in the new location when the service is restarted in step 3.</span></span> <span data-ttu-id="7b0fb-198">在重新啟動服務之前，tempdb 將繼續使用現有位置中的資料和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-198">Until the service is restarted, tempdb continues to use the data and log files in existing location.</span></span>  
  
1.  <span data-ttu-id="7b0fb-199">判斷 `tempdb` 資料庫的邏輯檔案名稱以及它們目前的磁碟位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-199">Determine the logical file names of the `tempdb` database and their current location on the disk.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    GO  
    ```  
  
2.  <span data-ttu-id="7b0fb-200">請利用 `ALTER DATABASE`來變更每個檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-200">Change the location of each file by using `ALTER DATABASE`.</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'F:\SQLLog\templog.ldf');  
    GO  
    ```  
  
3.  <span data-ttu-id="7b0fb-201">停止和重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-201">Stop and restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="7b0fb-202">確認檔案變更。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-202">Verify the file change.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    ```  
  
5.  <span data-ttu-id="7b0fb-203">從原始位置刪除 `tempdb.mdf` 和 `templog.ldf` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b0fb-203">Delete the `tempdb.mdf` and `templog.ldf` files from the original location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b0fb-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b0fb-204">See Also</span></span>  
 <span data-ttu-id="7b0fb-205">[Resource 資料庫](resource-database.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-205">[Resource Database](resource-database.md) </span></span>  
 <span data-ttu-id="7b0fb-206">[tempdb 資料庫](tempdb-database.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-206">[tempdb Database](tempdb-database.md) </span></span>  
 <span data-ttu-id="7b0fb-207">[master 資料庫](master-database.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-207">[master Database](master-database.md) </span></span>  
 <span data-ttu-id="7b0fb-208">[msdb 資料庫](msdb-database.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-208">[msdb Database](msdb-database.md) </span></span>  
 <span data-ttu-id="7b0fb-209">[Model 資料庫](model-database.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-209">[model Database](model-database.md) </span></span>  
 <span data-ttu-id="7b0fb-210">[移動使用者資料庫](move-user-databases.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-210">[Move User Databases](move-user-databases.md) </span></span>  
 <span data-ttu-id="7b0fb-211">[移動資料庫檔案](move-database-files.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-211">[Move Database Files](move-database-files.md) </span></span>  
 <span data-ttu-id="7b0fb-212">[啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-212">[Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) </span></span>  
 <span data-ttu-id="7b0fb-213">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7b0fb-213">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="7b0fb-214">重建系統資料庫</span><span class="sxs-lookup"><span data-stu-id="7b0fb-214">Rebuild System Databases</span></span>](system-databases.md)  
  
  
