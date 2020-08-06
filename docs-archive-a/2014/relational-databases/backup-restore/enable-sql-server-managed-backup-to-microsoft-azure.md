---
title: 設定 SQL Server 受控備份至 Azure |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9e3b86fde91028106263310aad8a1952fc041a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599524"
---
# <a name="setting-up-sql-server-managed-backup-to-azure"></a><span data-ttu-id="24917-102">設定 SQL Server Managed Backup 到 Azure</span><span class="sxs-lookup"><span data-stu-id="24917-102">Setting up SQL Server Managed Backup to Azure</span></span>
  <span data-ttu-id="24917-103">本主題包含兩個教學課程：</span><span class="sxs-lookup"><span data-stu-id="24917-103">This topic includes two tutorials:</span></span>  
  
 <span data-ttu-id="24917-104">在資料庫層級設定[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]、啟用電子郵件通知，以及監視備份活動。</span><span class="sxs-lookup"><span data-stu-id="24917-104">Set up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the database level, enable email notification, and monitor backup activity.</span></span>  
  
 <span data-ttu-id="24917-105">在執行個體層級設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]、啟用電子郵件通知，以及監視備份活動。</span><span class="sxs-lookup"><span data-stu-id="24917-105">Setting up  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the instance level, enable email notification, and monitor backup activity.</span></span>  
  
 <span data-ttu-id="24917-106">如需設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 可用性群組的教學課程，請參閱[將 SQL Server Managed 備份設定為可用性群組的 Microsoft Azure](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="24917-106">For a tutorial on setting up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for Availability Groups, see [Setting up SQL Server Managed Backup to Microsoft Azure for Availability Groups](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
## <a name="setting-up-ss_smartbackup"></a><span data-ttu-id="24917-107">設定[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24917-107">Setting Up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span></span>  
  
### <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><span data-ttu-id="24917-108">啟用及設定資料庫的 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24917-108">Enable and Configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a Database</span></span>  
 <span data-ttu-id="24917-109">此教學課程會先說明啟用及設定資料庫 (TestDB) 之 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的必要步驟，然後再說明啟用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 健全狀態之監視功能的步驟。</span><span class="sxs-lookup"><span data-stu-id="24917-109">This tutorial describes the steps necessary to enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a database (TestDB), followed by steps to enable monitoring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
 <span data-ttu-id="24917-110">**權限：**</span><span class="sxs-lookup"><span data-stu-id="24917-110">**Permissions:**</span></span>  
  
-   <span data-ttu-id="24917-111">需要**db_backupoperator**資料庫角色中的成員資格、具有**ALTER ANY CREDENTIAL**許可權，以及 `EXECUTE` **sp_delete_backuphistory**預存程式的許可權。</span><span class="sxs-lookup"><span data-stu-id="24917-111">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="24917-112">需要**smart_admin. fn_get_current_xevent_settings**函數的**SELECT**許可權。</span><span class="sxs-lookup"><span data-stu-id="24917-112">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="24917-113">需要 `EXECUTE` smart_admin 的許可權 **。 sp_get_backup_diagnostics**預存程式。</span><span class="sxs-lookup"><span data-stu-id="24917-113">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="24917-114">除此之外，因為它會從內部呼叫其他需要此權限的系統物件，所以還需要 `VIEW SERVER STATE` 權限。</span><span class="sxs-lookup"><span data-stu-id="24917-114">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
-   <span data-ttu-id="24917-115">需要 `EXECUTE` `smart_admin.sp_set_instance_backup` 和 `smart_admin.sp_backup_master_switch` 預存程式的許可權。</span><span class="sxs-lookup"><span data-stu-id="24917-115">Requires `EXECUTE` permissions on the `smart_admin.sp_set_instance_backup` and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  


1.  <span data-ttu-id="24917-116">**建立 Microsoft Azure 儲存體帳戶：** 備份會儲存在 Microsoft Azure 儲存體服務中。</span><span class="sxs-lookup"><span data-stu-id="24917-116">**Create a Microsoft Azure storage account:** The backups are stored in the Microsoft Azure storage service.</span></span> <span data-ttu-id="24917-117">如果您還沒有帳戶，您必須先建立 Microsoft Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="24917-117">You must first create a Microsoft Azure storage account, if you do not already have an account.</span></span>
    - <span data-ttu-id="24917-118">SQL Server 2014 使用分頁 blob，其不同于區塊和附加 blob。</span><span class="sxs-lookup"><span data-stu-id="24917-118">SQL Server 2014 uses page blobs, which are different than block and append blobs.</span></span> <span data-ttu-id="24917-119">因此，您必須建立一般用途帳戶，而不是 blob 帳戶。</span><span class="sxs-lookup"><span data-stu-id="24917-119">Therefore you must create a general purpose account, and not a blob account.</span></span> <span data-ttu-id="24917-120">如需詳細資訊，請參閱[關於 Azure 儲存體帳戶](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)。</span><span class="sxs-lookup"><span data-stu-id="24917-120">For more information, see [About Azure storage accounts](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span>
    - <span data-ttu-id="24917-121">記下儲存體帳戶名稱和存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="24917-121">Make a note of the storage account name, and the access keys.</span></span> <span data-ttu-id="24917-122">儲存體帳戶名稱和存取金鑰資訊可用來建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="24917-122">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="24917-123">SQL 認證會用來驗證儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="24917-123">The SQL Credential is used to authenticate to the storage account.</span></span>  
 
2.  <span data-ttu-id="24917-124">**建立 SQL 認證：** 使用儲存體帳戶的名稱做為身分識別，並使用儲存體存取金鑰做為密碼，以建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="24917-124">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="24917-125">**確定 SQL Server Agent 服務已啟動且正在執行：** 如果目前未執行，請啟動 SQL Server Agent。</span><span class="sxs-lookup"><span data-stu-id="24917-125">**Ensure SQL Server Agent service is Started and Running:**  Start SQL Server Agent if it is not currently running.</span></span>  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="24917-126">需要在執行個體上執行 SQL Server Agent，才能執行備份作業。</span><span class="sxs-lookup"><span data-stu-id="24917-126">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="24917-127">您可能需要將 SQL Server Agent 設定為自動執行，以確保備份作業定期執行。</span><span class="sxs-lookup"><span data-stu-id="24917-127">You may want to set SQL Server Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="24917-128">**決定保留期限：** 決定備份檔案的保留期限。</span><span class="sxs-lookup"><span data-stu-id="24917-128">**Determine the retention period:** Determine the retention period for the backup files.</span></span> <span data-ttu-id="24917-129">保留週期的指定單位為天，範圍從 1 到 30。</span><span class="sxs-lookup"><span data-stu-id="24917-129">The retention period is specified in days and can range from 1 to 30.</span></span>  
  
5.  <span data-ttu-id="24917-130">**啟用和設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ：** 啟動 SQL Server Management Studio，並連接到安裝資料庫的實例。</span><span class="sxs-lookup"><span data-stu-id="24917-130">**Enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Start SQL Server Management Studio and connect to the instance where the database is installed.</span></span> <span data-ttu-id="24917-131">在您根據需要修改資料庫名稱、SQL 認證、保留週期及加密選項的值之後，請在查詢視窗中執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="24917-131">From the query window run the following statement after you modify the values for the database name, SQL Credential, retention period, and encryption options per your requirements:</span></span>  
  
     <span data-ttu-id="24917-132">如需建立憑證以進行加密的詳細資訊，請參閱[建立加密備份](create-an-encrypted-backup.md)中的**建立備份憑證**步驟。</span><span class="sxs-lookup"><span data-stu-id="24917-132">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="24917-133">已在您指定的資料庫上啟用。</span><span class="sxs-lookup"><span data-stu-id="24917-133">is now enabled on the database you specified.</span></span> <span data-ttu-id="24917-134">資料庫上的備份作業可能需要 15 分鐘才會開始執行。</span><span class="sxs-lookup"><span data-stu-id="24917-134">It may take up to 15 minutes for the backup operations on the database to start to run.</span></span>  
  
6.  <span data-ttu-id="24917-135">**檢閱延伸事件預設設定：** 執行下列 Transact-SQL 陳述式，以檢閱擴充事件設定。</span><span class="sxs-lookup"><span data-stu-id="24917-135">**Review Extended Event Default Configuration:** Review the Extended Event settings by running the following transact-SQL statement.</span></span>  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     <span data-ttu-id="24917-136">預設會顯示已經啟用 Admin、Operational 和 Analytical 通道事件，且無法予以停用。</span><span class="sxs-lookup"><span data-stu-id="24917-136">You should see that Admin, Operational, and Analytical channel events are enabled by default and cannot be disabled.</span></span> <span data-ttu-id="24917-137">這應該足以監視需要手動介入的事件。</span><span class="sxs-lookup"><span data-stu-id="24917-137">This should be sufficient to monitor the events that require manual intervention.</span></span>  <span data-ttu-id="24917-138">您可以啟用偵錯事件，不過偵錯通道包含 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 用來偵測及解決問題的資訊和偵錯事件。</span><span class="sxs-lookup"><span data-stu-id="24917-138">You can enable debug events, but the debug channels include informational and debug events that [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] uses to detect issues and solve them.</span></span> <span data-ttu-id="24917-139">如需詳細資訊，請參閱[Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="24917-139">For more information, see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
7.  <span data-ttu-id="24917-140">**啟用及設定健全狀態通知：** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的預存程序會建立代理程式作業，以針對可能需要注意的錯誤或警告傳送電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="24917-140">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span> <span data-ttu-id="24917-141">下列步驟描述啟用及設定電子郵件通知的程序：</span><span class="sxs-lookup"><span data-stu-id="24917-141">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="24917-142">如果執行個體上尚未啟用，請設定 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="24917-142">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="24917-143">如需詳細資訊，請參閱＜ [Configure Database Mail](../database-mail/configure-database-mail.md)＞。</span><span class="sxs-lookup"><span data-stu-id="24917-143">For more information, see [Configure Database Mail](../database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="24917-144">設定 SQL Server Agent 通知使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="24917-144">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="24917-145">如需詳細資訊，請參閱 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="24917-145">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="24917-146">**啟用電子郵件通知接收備份錯誤和警告：** 從 [查詢] 視窗中，執行下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="24917-146">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         <span data-ttu-id="24917-147">如需詳細資訊和完整的範例腳本，請參閱[Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="24917-147">For more information, and a full sample script see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
8.  <span data-ttu-id="24917-148">**檢視 Microsoft Azure 儲存體帳戶中的備份檔案：** 從 SQL Server Management Studio 或 Azure 管理入口網站連接至儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="24917-148">**View backup files in the Microsoft Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="24917-149">您會看到裝載設定為使用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的資料庫之 SQL Server 執行個體的容器。</span><span class="sxs-lookup"><span data-stu-id="24917-149">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="24917-150">您也會在啟用資料庫之 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的 15 分鐘內，看到資料庫和記錄備份。</span><span class="sxs-lookup"><span data-stu-id="24917-150">You may also see a database and a log backup within 15 minutes of enabling [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the database.</span></span>  
  
9. <span data-ttu-id="24917-151">**監視健康狀態：** 您可以透過先前設定的電子郵件通知進行監視，或主動監視記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="24917-151">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="24917-152">以下是用於檢視事件的一些 Transact-SQL 陳述式範例：</span><span class="sxs-lookup"><span data-stu-id="24917-152">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 <span data-ttu-id="24917-153">本節所描述的步驟是針對第一次在資料庫上設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="24917-153">The steps described in this section are specifically for configuring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the first time on the database.</span></span> <span data-ttu-id="24917-154">您可以使用相同的系統預存程式 smart_admin 來修改現有的設定 **。 sp_set_db_backup**並提供新的值。</span><span class="sxs-lookup"><span data-stu-id="24917-154">You can modify the existing configurations using the same system stored procedure **smart_admin.sp_set_db_backup** and provide the new values.</span></span> <span data-ttu-id="24917-155">如需詳細資訊，請參閱[SQL Server Managed Backup to Microsoft Azure-保留和儲存體設定](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="24917-155">For more information, see [SQL Server Managed Backup to Microsoft Azure - Retention and Storage Settings](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
### <a name="enable-ss_smartbackup-for-the-instance-with-default-settings"></a><span data-ttu-id="24917-156">使用預設設定啟用執行個體的 </span><span class="sxs-lookup"><span data-stu-id="24917-156">Enable [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the Instance with Default Settings</span></span>  
 <span data-ttu-id="24917-157">本教學課程描述啟用及設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 實例 ' MyInstance ' 的步驟 \\ 。</span><span class="sxs-lookup"><span data-stu-id="24917-157">This tutorial describes the steps to enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the instance, 'MyInstance',\\.</span></span> <span data-ttu-id="24917-158">其中也包括如何啟用[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]健全狀態之監視功能的步驟。</span><span class="sxs-lookup"><span data-stu-id="24917-158">It includes steps to enable monitoring the [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
 <span data-ttu-id="24917-159">**權限：**</span><span class="sxs-lookup"><span data-stu-id="24917-159">**Permissions:**</span></span>  
  
-   <span data-ttu-id="24917-160">需要**db_backupoperator**資料庫角色中的成員資格、具有**ALTER ANY CREDENTIAL**許可權，以及 `EXECUTE` **sp_delete_backuphistory**預存程式的許可權。</span><span class="sxs-lookup"><span data-stu-id="24917-160">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="24917-161">需要**smart_admin. fn_get_current_xevent_settings**函數的**SELECT**許可權。</span><span class="sxs-lookup"><span data-stu-id="24917-161">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="24917-162">需要 `EXECUTE` smart_admin 的許可權 **。 sp_get_backup_diagnostics**預存程式。</span><span class="sxs-lookup"><span data-stu-id="24917-162">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="24917-163">除此之外，因為它會從內部呼叫其他需要此權限的系統物件，所以還需要 `VIEW SERVER STATE` 權限。</span><span class="sxs-lookup"><span data-stu-id="24917-163">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  


1.  <span data-ttu-id="24917-164">**建立 Microsoft Azure 儲存體帳戶：** 備份會儲存在 Microsoft Azure 儲存體服務中。</span><span class="sxs-lookup"><span data-stu-id="24917-164">**Create a Microsoft Azure storage account:** The backups are stored in the Microsoft Azure storage service.</span></span> <span data-ttu-id="24917-165">如果您還沒有帳戶，您必須先建立 Microsoft Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="24917-165">You must first create a Microsoft Azure storage account, if you do not already have an account.</span></span>
    - <span data-ttu-id="24917-166">SQL Server 2014 使用分頁 blob，其不同于區塊和附加 blob。</span><span class="sxs-lookup"><span data-stu-id="24917-166">SQL Server 2014 uses page blobs, which are different than block and append blobs.</span></span> <span data-ttu-id="24917-167">因此，您必須建立一般用途帳戶，而不是 blob 帳戶。</span><span class="sxs-lookup"><span data-stu-id="24917-167">Therefore you must create a general purpose account, and not a blob account.</span></span> <span data-ttu-id="24917-168">如需詳細資訊，請參閱[關於 Azure 儲存體帳戶](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)。</span><span class="sxs-lookup"><span data-stu-id="24917-168">For more information, see [About Azure storage accounts](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span>
    - <span data-ttu-id="24917-169">記下儲存體帳戶名稱和存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="24917-169">Make a note of the storage account name, and the access keys.</span></span> <span data-ttu-id="24917-170">儲存體帳戶名稱和存取金鑰資訊可用來建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="24917-170">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="24917-171">SQL 認證會用來驗證儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="24917-171">The SQL Credential is used to authenticate to the storage account.</span></span>  
  
2.  <span data-ttu-id="24917-172">**建立 SQL 認證：** 使用儲存體帳戶的名稱做為身分識別，並使用儲存體存取金鑰做為密碼，以建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="24917-172">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="24917-173">**確認 SQL Server Agent 服務已啟動且在執行中：** 如果目前尚未執行 SQL Server Agent，請加以啟動。</span><span class="sxs-lookup"><span data-stu-id="24917-173">**Ensure SQL Server Agent service is Started and Running:** Start SQL Server Agent if it is not currently running.</span></span> [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="24917-174">需要在執行個體上執行 SQL Server Agent，才能執行備份作業。</span><span class="sxs-lookup"><span data-stu-id="24917-174">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="24917-175">您可能需要將 SQL Server Agent 設定為自動執行，以確保備份作業定期執行。</span><span class="sxs-lookup"><span data-stu-id="24917-175">You may want to set SQL Server Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="24917-176">**決定保留期限：** 決定備份檔案的保留期限。</span><span class="sxs-lookup"><span data-stu-id="24917-176">**Determine the retention period:** Determine the retention period for the backup files.</span></span> <span data-ttu-id="24917-177">保留週期的指定單位為天，範圍從 1 到 30。</span><span class="sxs-lookup"><span data-stu-id="24917-177">The retention period is specified in days and can range from 1 to 30.</span></span> <span data-ttu-id="24917-178">在執行個體層級啟用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 並使用預設值之後，所有於此後所新建的資料庫，皆會繼承這些設定。</span><span class="sxs-lookup"><span data-stu-id="24917-178">Once [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] is enabled at the instance level with the defaults all new databases created thereafter will inherit the settings.</span></span> <span data-ttu-id="24917-179">僅支援設定為完整或大量記錄復原模式的資料庫，並且會自動設定。</span><span class="sxs-lookup"><span data-stu-id="24917-179">Only databases that are set to full or bulk-logged recovery models are supported and will be configured automatically.</span></span> <span data-ttu-id="24917-180">如果您不想設定[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]，您可以隨時停用特定資料庫的[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24917-180">You may disable [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a specific database at any time if you  do not want [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configured.</span></span> <span data-ttu-id="24917-181">您也可以在資料庫層級設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]，以變更特定資料庫的設定。</span><span class="sxs-lookup"><span data-stu-id="24917-181">You can also change the configuration for a specific database by configuring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the database level.</span></span>  
  
5.  <span data-ttu-id="24917-182">**啟用和設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ：** 啟動 SQL Server Management Studio，並連接到 SQL Server 的實例。</span><span class="sxs-lookup"><span data-stu-id="24917-182">**Enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Start SQL Server Management Studio and connect to the instance of SQL Server.</span></span> <span data-ttu-id="24917-183">在您根據需要修改資料庫名稱、SQL 認證、保留週期及加密選項的值之後，請在查詢視窗中執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="24917-183">From the query window run the following statement after you modify the values for the database name, SQL Credential, retention period, and the encryption options per your requirements:</span></span>  
  
     <span data-ttu-id="24917-184">如需建立憑證以進行加密的詳細資訊，請參閱[建立加密備份](create-an-encrypted-backup.md)中的**建立備份憑證**步驟。</span><span class="sxs-lookup"><span data-stu-id="24917-184">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     <span data-ttu-id="24917-185">現在在執行個體上已啟用[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24917-185">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] is now enabled on the instance.</span></span>  
  
6.  <span data-ttu-id="24917-186">執行下列 Transact-SQL 陳述式，以驗證組態設定：</span><span class="sxs-lookup"><span data-stu-id="24917-186">Verify the configuration settings by running the following Transact-SQL statement:</span></span>  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  <span data-ttu-id="24917-187">在執行個體上建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="24917-187">Create a new database on the instance.</span></span> <span data-ttu-id="24917-188">執行下列 Transact-SQL 陳述式，以檢視資料庫的 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 組態設定：</span><span class="sxs-lookup"><span data-stu-id="24917-188">Run the following Transact-SQL statement to view the [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configuration settings for the database:</span></span>  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     <span data-ttu-id="24917-189">可能需要 15 分鐘才會顯示設定，並開始執行資料庫上的備份作業。</span><span class="sxs-lookup"><span data-stu-id="24917-189">It may take up to 15 minutes for the settings to show and backup operations on the database to start to run.</span></span>  
  
8.  <span data-ttu-id="24917-190">**啟用及設定健全狀態通知：** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的預存程序會建立代理程式作業，以針對可能需要注意的錯誤或警告傳送電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="24917-190">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span>  <span data-ttu-id="24917-191">若要接收這類通知，必須啟用 [執行預存程序]，以建立 SQL Server Agent 工作。</span><span class="sxs-lookup"><span data-stu-id="24917-191">To receive such notifications, you must enable run the stored procedure which creates a SQL Server Agent Job.</span></span> <span data-ttu-id="24917-192">下列步驟描述啟用及設定電子郵件通知的程序：</span><span class="sxs-lookup"><span data-stu-id="24917-192">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="24917-193">如果執行個體上尚未啟用，請設定 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="24917-193">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="24917-194">如需詳細資訊，請參閱＜ [Configure Database Mail](../database-mail/configure-database-mail.md)＞。</span><span class="sxs-lookup"><span data-stu-id="24917-194">For more information, see [Configure Database Mail](../database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="24917-195">設定 SQL Server Agent 通知使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="24917-195">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="24917-196">如需詳細資訊，請參閱 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="24917-196">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="24917-197">**啟用電子郵件通知接收備份錯誤和警告：** 從 [查詢] 視窗中，執行下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="24917-197">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         <span data-ttu-id="24917-198">如需有關如何監視的詳細資訊，以及完整的範例腳本，請參閱[monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="24917-198">For more information about how to monitor, and a full sample script see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
9. <span data-ttu-id="24917-199">**檢視 Microsoft Azure 儲存體帳戶中的備份檔案：** 從 SQL Server Management Studio 或 Azure 管理入口網站連接至儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="24917-199">**View backup files in the Microsoft Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="24917-200">您會看到裝載設定為使用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的資料庫之 SQL Server 執行個體的容器。</span><span class="sxs-lookup"><span data-stu-id="24917-200">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="24917-201">您也會在建立新的資料庫之後的 15 分鐘內，看到資料庫和記錄備份。</span><span class="sxs-lookup"><span data-stu-id="24917-201">You may also see a database and a log backup within 15 minutes of creating a new database.</span></span>  
  
10. <span data-ttu-id="24917-202">**監視健康狀態：** 您可以透過先前設定的電子郵件通知進行監視，或主動監視記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="24917-202">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="24917-203">以下是用於檢視事件的一些 Transact-SQL 陳述式範例：</span><span class="sxs-lookup"><span data-stu-id="24917-203">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 <span data-ttu-id="24917-204">在資料庫層級明確地配置設定，可以覆寫特定資料庫的 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 預設設定。</span><span class="sxs-lookup"><span data-stu-id="24917-204">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] default settings can be overridden for a specific database by configuring the settings specifically at the database level.</span></span> <span data-ttu-id="24917-205">您也可以暫停再繼續執行 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="24917-205">You can also pause and resume [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] service temporarily.</span></span> <span data-ttu-id="24917-206">如需詳細資訊，請參閱[SQL Server Managed Backup to Microsoft Azure-保留和儲存體設定](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)</span><span class="sxs-lookup"><span data-stu-id="24917-206">For more information, see [SQL Server Managed Backup to Microsoft Azure - Retention and Storage Settings](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)</span></span>  
  
  
