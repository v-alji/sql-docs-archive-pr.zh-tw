---
title: SQL Server 備份至 URL 的最佳做法和疑難排解 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06127b5e4b422750554c30fae23b6190107cb643
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597174"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a><span data-ttu-id="62a28-102">SQL Server 備份至 URL 的最佳作法和疑難排解</span><span class="sxs-lookup"><span data-stu-id="62a28-102">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>
  <span data-ttu-id="62a28-103">本主題包含從 SQL Server 備份及還原至 Azure Blob 服務的最佳做法和疑難排解提示。</span><span class="sxs-lookup"><span data-stu-id="62a28-103">This topic includes best practices and troubleshooting tips for SQL Server backup and restores to the Azure Blob service.</span></span>  
  
 <span data-ttu-id="62a28-104">如需有關使用 Azure Blob 儲存體服務進行 SQL Server 備份或還原作業的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="62a28-104">For more information about using Azure Blob storage service for SQL Server backup or restore operations, see:</span></span>  
  
-   [<span data-ttu-id="62a28-105">使用 Azure Blob 儲存體服務的 SQL Server 備份及還原</span><span class="sxs-lookup"><span data-stu-id="62a28-105">SQL Server Backup and Restore with Azure Blob Storage Service</span></span>](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [<span data-ttu-id="62a28-106">教學課程：SQL Server 備份及還原至 Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="62a28-106">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a><span data-ttu-id="62a28-107">管理備份</span><span class="sxs-lookup"><span data-stu-id="62a28-107">Managing Backups</span></span>  
 <span data-ttu-id="62a28-108">下列清單包含管理備份的一般建議：</span><span class="sxs-lookup"><span data-stu-id="62a28-108">The following list includes general recommendations to manage backups:</span></span>  
  
-   <span data-ttu-id="62a28-109">建議針對每個備份使用唯一的檔案名稱，避免不小心覆寫 Blob。</span><span class="sxs-lookup"><span data-stu-id="62a28-109">Unique file name for every backup is recommended to prevent accidentally overwriting the blobs.</span></span>  
  
-   <span data-ttu-id="62a28-110">建立容器時，建議您將存取層級設定為 [私用]  ，如此只有能夠提供必要驗證資訊的使用者或帳戶才能讀取或寫入容器中的 Blob。</span><span class="sxs-lookup"><span data-stu-id="62a28-110">When creating a container, it is recommended that you set the access level to **private**, so only users or accounts that can provide the required authentication information can read or write the blobs in the container.</span></span>  
  
-   <span data-ttu-id="62a28-111">針對在 Azure 虛擬機器中執行 SQL Server 實例上 SQL Server 資料庫，請使用與虛擬機器位於相同區域中的儲存體帳戶，以避免區域之間的資料傳輸成本。</span><span class="sxs-lookup"><span data-stu-id="62a28-111">For SQL Server databases on an instance of SQL Server running in an Azure Virtual Machine, use a storage account in the same region as the virtual machine to avoid data transfer costs between regions.</span></span> <span data-ttu-id="62a28-112">使用相同的地區也可以確保備份與還原作業達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="62a28-112">Using the same region also ensures optimal performance for backup and restore operations.</span></span>  
  
-   <span data-ttu-id="62a28-113">失敗的備份活動可能會產生無效的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="62a28-113">Failed backup activity can result in an invalid backup file.</span></span> <span data-ttu-id="62a28-114">我們建議您定期識別失敗的備份並刪除 Blob 檔案。</span><span class="sxs-lookup"><span data-stu-id="62a28-114">We recommend periodic identification of failed backups and deleting the blob files.</span></span> <span data-ttu-id="62a28-115">如需詳細資訊，請參閱[刪除擁有使用中租用的備份 Blob 檔案](deleting-backup-blob-files-with-active-leases.md)</span><span class="sxs-lookup"><span data-stu-id="62a28-115">For more information, see [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)</span></span>  
  
-   <span data-ttu-id="62a28-116">在備份期間使用 `WITH COMPRESSION` 選項可以將您的儲存體成本和儲存體交易成本降到最低程度。</span><span class="sxs-lookup"><span data-stu-id="62a28-116">Using the `WITH COMPRESSION` option during backup can minimize your storage costs and storage transaction costs.</span></span> <span data-ttu-id="62a28-117">它也可以減少完成備份程序所需的時間。</span><span class="sxs-lookup"><span data-stu-id="62a28-117">It can also decrease the time taken to complete the backup process.</span></span>  
  
## <a name="handling-large-files"></a><span data-ttu-id="62a28-118">處理大型檔案</span><span class="sxs-lookup"><span data-stu-id="62a28-118">Handling Large Files</span></span>  
  
-   <span data-ttu-id="62a28-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份作業會使用多個執行緒來最佳化 Azure Blob 儲存體服務的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="62a28-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup operation uses multiple threads to optimize data transfer to Azure Blob storage services.</span></span>  <span data-ttu-id="62a28-120">不過，其效能取決於各種因素，例如 ISV 頻寬和資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="62a28-120">However the performance depends on various factors, such as ISV bandwidth and size of the database.</span></span> <span data-ttu-id="62a28-121">如果您計畫要備份內部部署 SQL Server 資料庫中的大型資料庫或檔案群組，建議您先進行一些輸送量測試。</span><span class="sxs-lookup"><span data-stu-id="62a28-121">If you plan to back up large databases or filegroups from an on-premise SQL Server database, it is recommended that you do some throughput testing first.</span></span> <span data-ttu-id="62a28-122">[Azure 儲存體 SLA](https://go.microsoft.com/fwlink/?LinkId=271619)具有 blob 的最長處理時間，您可以將其納入考慮。</span><span class="sxs-lookup"><span data-stu-id="62a28-122">[Azure storage SLA's](https://go.microsoft.com/fwlink/?LinkId=271619) have maximum processing times for blobs that you can take into consideration.</span></span>  
  
-   <span data-ttu-id="62a28-123">備份大型檔案時，務必遵循**管理備份**一節中的建議使用 `WITH COMPRESSION` 選項。</span><span class="sxs-lookup"><span data-stu-id="62a28-123">Using the `WITH COMPRESSION` option as recommended in the **Managing Backup** section, it is very important when backing up large files.</span></span>  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a><span data-ttu-id="62a28-124">疑難排解備份至 URL 或從中還原</span><span class="sxs-lookup"><span data-stu-id="62a28-124">Troubleshooting Backup To or Restore from URL</span></span>  
 <span data-ttu-id="62a28-125">以下是對備份至 Azure Blob 儲存體服務或從中還原時發生的錯誤，進行疑難排解的一些快速方法。</span><span class="sxs-lookup"><span data-stu-id="62a28-125">Following are some quick ways to troubleshoot errors when backing up to or restoring from the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="62a28-126">為避免由於不支援的選項或限制而發生錯誤，請參閱[SQL Server 備份和還原與 Azure Blob 儲存體服務](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)一文中的限制清單，以及支援 BACKUP 和 restore 命令的資訊。</span><span class="sxs-lookup"><span data-stu-id="62a28-126">To avoid errors due to unsupported options or limitations, review the list of limitations, and support for BACKUP and RESTORE commands information in the [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) article.</span></span>  
  
 <span data-ttu-id="62a28-127">**驗證錯誤：**</span><span class="sxs-lookup"><span data-stu-id="62a28-127">**Authentication Errors:**</span></span>  
  
-   <span data-ttu-id="62a28-128">WITH CREDENTIAL 是新的選項，而且需要備份至 Azure Blob 儲存體服務或從中還原。</span><span class="sxs-lookup"><span data-stu-id="62a28-128">WITH CREDENTIAL is a new option and required to back up to or restore from the Azure Blob storage service.</span></span> <span data-ttu-id="62a28-129">與認證有關的失敗可能包括：</span><span class="sxs-lookup"><span data-stu-id="62a28-129">Failures related to credential could be the following:</span></span>  
  
     <span data-ttu-id="62a28-130">`BACKUP` 或 `RESTORE` 命令中指定的認證不存在。</span><span class="sxs-lookup"><span data-stu-id="62a28-130">The credential specified in the `BACKUP` or `RESTORE` command does not exist.</span></span> <span data-ttu-id="62a28-131">若要避免此問題，您可以在 Backup 陳述式中加入 T-SQL 陳述式來建立認證 (如果認證不存在的話)。</span><span class="sxs-lookup"><span data-stu-id="62a28-131">To avoid this issue, you can include T-SQL statements to create the credential if one does not exist in the backup statement.</span></span> <span data-ttu-id="62a28-132">以下是您可以使用的範例：</span><span class="sxs-lookup"><span data-stu-id="62a28-132">The following is an example you can use:</span></span>  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   <span data-ttu-id="62a28-133">認證存在，但是用來執行 Backup 命令的登入帳戶沒有存取認證的權限。</span><span class="sxs-lookup"><span data-stu-id="62a28-133">The credential exists but the login account that is used to run the backup command does not have permissions to access the credentials.</span></span> <span data-ttu-id="62a28-134">請使用具備 **更改任何認證** 權限的 **db_backupoperator** 角色登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="62a28-134">Use a login account in the **db_backupoperator** role with **Alter any credential** permissions.</span></span>  
  
-   <span data-ttu-id="62a28-135">確認儲存體帳戶名稱與金鑰值。</span><span class="sxs-lookup"><span data-stu-id="62a28-135">Verify the storage account name and key values.</span></span> <span data-ttu-id="62a28-136">儲存在認證中的資訊必須符合您在備份和還原作業中使用之 Azure 儲存體帳戶的屬性值。</span><span class="sxs-lookup"><span data-stu-id="62a28-136">The information stored in the credential must match the property values of the Azure storage account you are using in the backup and restore operations.</span></span>  
  
 <span data-ttu-id="62a28-137">**備份錯誤/失敗：**</span><span class="sxs-lookup"><span data-stu-id="62a28-137">**Backup Errors/Failures:**</span></span>  
  
-   <span data-ttu-id="62a28-138">相同 Blob 的平行備份會導致其中一個備份失敗並出現 [初始化失敗]  錯誤。</span><span class="sxs-lookup"><span data-stu-id="62a28-138">Parallel backups to the same blob cause one of the backups to fail with an **Initialization failed** error.</span></span>  
  
-   <span data-ttu-id="62a28-139">使用下列錯誤記錄來協助疑難排解備份錯誤：</span><span class="sxs-lookup"><span data-stu-id="62a28-139">Use the following error logs to help with troubleshooting backup errors:</span></span>  
  
    -   <span data-ttu-id="62a28-140">您可以使用下列格式來設定追蹤旗標 3051，以便記錄至特定錯誤記錄：</span><span class="sxs-lookup"><span data-stu-id="62a28-140">Set trace flag 3051 to turn on logging to a specific error log with the following format in:</span></span>  
  
         <span data-ttu-id="62a28-141">BackupToUrl- \<instname> - \<dbname> -action- \<PID> .log，其中 \<action> 是下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="62a28-141">BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log Where \<action> is one of:</span></span>  
  
        -   `DB`  
  
        -   `FILELISTONLY`  
  
        -   `LABELONLY`  
  
        -   `HEADERONLY`  
  
        -   `VERIFYONLY`  
  
    -   <span data-ttu-id="62a28-142">您也可以藉由查看 Windows 事件記錄檔（位於名為 ' SQLBackupToUrl ' 的應用程式記錄底下）來尋找資訊。</span><span class="sxs-lookup"><span data-stu-id="62a28-142">You can also find information by reviewing the Windows Event Log - Under Application logs with the name 'SQLBackupToUrl'.</span></span>  
  
-   <span data-ttu-id="62a28-143">從壓縮備份還原時，您可能會看見下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="62a28-143">When restoring from a compressed backup, you might see the following error:</span></span>  
  
    -   <span data-ttu-id="62a28-144">**發生 SqlException 3284。嚴重性：16狀態：5**</span><span class="sxs-lookup"><span data-stu-id="62a28-144">**SqlException 3284 occurred. Severity: 16 State: 5**</span></span>  
        <span data-ttu-id="62a28-145">**裝置 ' ' 上的訊息標記 https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak 未對齊。以用來建立 backupset 的相同區塊大小重新發出 Restore 語句： ' 65536 ' 看起來像是可能的值。**</span><span class="sxs-lookup"><span data-stu-id="62a28-145">**Message Filemark on device 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak' is not aligned. Reissue the Restore statement with the same block size used to create the backupset: '65536' looks like a possible value.**</span></span>  
  
         <span data-ttu-id="62a28-146">若要解決此錯誤，請重新發出指定 `BACKUP` 的 `BLOCKSIZE = 65536` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="62a28-146">To solve this error, reissue the `BACKUP` statement with `BLOCKSIZE = 65536` specified.</span></span>  
  
-   <span data-ttu-id="62a28-147">含有使用中租用的 Blob 導致備份期間發生錯誤：失敗的備份活動可能會產生含有使用中租用的 Blob。</span><span class="sxs-lookup"><span data-stu-id="62a28-147">Error during backup due to blobs that have active lease on them: Failed backup activity can result in blobs with active leases.</span></span>  
  
     <span data-ttu-id="62a28-148">如果重新嘗試執行 Backup 陳述式，備份作業可能會失敗並出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="62a28-148">If a backup statement is reattempted, backup operation might fail with an error similar to the following:</span></span>  
  
     <span data-ttu-id="62a28-149">**Backup to URL 收到遠端端點的例外狀況。例外狀況訊息：遠端伺服器傳回錯誤：(412) Blob 目前存在租用，而且要求中並未指定任何租用識別碼**。</span><span class="sxs-lookup"><span data-stu-id="62a28-149">**Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (412) There is currently a lease on the blob and no lease ID was specified in the request**.</span></span>  
  
     <span data-ttu-id="62a28-150">如果針對擁有使用中租用的備份 Blob 檔案執行 Restore 陳述式，還原作業會失敗並出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="62a28-150">If a restore statement is attempted on a backup blob file that has an active lease, the restore operation fails with an error similar to the following:</span></span>  
  
     <span data-ttu-id="62a28-151">**例外狀況訊息: 遠端伺服器傳回錯誤: (409) 衝突。**</span><span class="sxs-lookup"><span data-stu-id="62a28-151">**Exception Message: The remote server returned an error: (409) Conflict..**</span></span>  
  
     <span data-ttu-id="62a28-152">發生這類錯誤時，您必須刪除 Blob 檔案。</span><span class="sxs-lookup"><span data-stu-id="62a28-152">When such error occurs, the blob files need to be deleted.</span></span> <span data-ttu-id="62a28-153">如需有關此案例以及如何更正這個問題的詳細資訊，請參閱 [刪除擁有使用中租用的備份 Blob 檔案](deleting-backup-blob-files-with-active-leases.md)</span><span class="sxs-lookup"><span data-stu-id="62a28-153">For more information on this scenario and how to correct this problem, see [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)</span></span>  
  
## <a name="proxy-errors"></a><span data-ttu-id="62a28-154">Proxy 錯誤</span><span class="sxs-lookup"><span data-stu-id="62a28-154">Proxy Errors</span></span>  
 <span data-ttu-id="62a28-155">如果您使用 Proxy 伺服器存取網際網路，可能會看見下列問題：</span><span class="sxs-lookup"><span data-stu-id="62a28-155">If you are using Proxy Servers to access the internet, you may see the following issues:</span></span>  
  
 <span data-ttu-id="62a28-156">**Proxy 伺服器連線節流：**</span><span class="sxs-lookup"><span data-stu-id="62a28-156">**Connection throttling by Proxy Servers:**</span></span>  
  
 <span data-ttu-id="62a28-157">Proxy 伺服器可能有限制每分鐘連接數目的設定。</span><span class="sxs-lookup"><span data-stu-id="62a28-157">Proxy Servers can have settings that limit the number of connections per minute.</span></span> <span data-ttu-id="62a28-158">備份至 URL 處理序是一個多執行緒處理序，因此可能會超出此限制。</span><span class="sxs-lookup"><span data-stu-id="62a28-158">The Backup to URL process is a multi-threaded process and hence can go over this limit.</span></span> <span data-ttu-id="62a28-159">如果發生這種情況，Proxy 伺服器會清除該連接。</span><span class="sxs-lookup"><span data-stu-id="62a28-159">If this happens, the proxy server kills the connection.</span></span> <span data-ttu-id="62a28-160">若要解決這個問題，請變更 Proxy 設定，讓 SQL Server 不使用 Proxy。</span><span class="sxs-lookup"><span data-stu-id="62a28-160">To resolve this issue, change the proxy settings so SQL Server is not using the proxy.</span></span>   <span data-ttu-id="62a28-161">以下是您可能在錯誤記錄檔中看到的類型或錯誤訊息的部分範例：</span><span class="sxs-lookup"><span data-stu-id="62a28-161">Following are some examples of the types or error messages you may see in the error log:</span></span>  
  
-   <span data-ttu-id="62a28-162">"" 的寫入 http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak 失敗：備份至 URL 收到來自遠端端點的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="62a28-162">Write on "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak" failed: Backup to URL received an exception from the remote endpoint.</span></span> <span data-ttu-id="62a28-163">例外狀況訊息: 無法讀取傳輸連線的資料: 此連接已經關閉。</span><span class="sxs-lookup"><span data-stu-id="62a28-163">Exception Message: Unable to read data from the transport connection: The connection was closed.</span></span>  
  
-   <span data-ttu-id="62a28-164">檔案 "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" 上發生無法復原的 I/O 錯誤。無法從遠端端點收集錯誤。</span><span class="sxs-lookup"><span data-stu-id="62a28-164">A nonrecoverable I/O error occurred on file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Error could not be gathered from Remote Endpoint.</span></span>  
  
     <span data-ttu-id="62a28-165">訊息 3013，層級 16，狀態 1，行 2</span><span class="sxs-lookup"><span data-stu-id="62a28-165">Msg 3013, Level 16, State 1, Line 2</span></span>  
  
     <span data-ttu-id="62a28-166">備份資料庫正在異常結束。</span><span class="sxs-lookup"><span data-stu-id="62a28-166">BACKUP DATABASE is terminating abnormally.</span></span>  
  
-   <span data-ttu-id="62a28-167">BackupIoRequest：： ReportIoError：備份裝置 ' ' 上的寫入失敗 http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak 。</span><span class="sxs-lookup"><span data-stu-id="62a28-167">BackupIoRequest::ReportIoError: write failure on backup device 'http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak'.</span></span> <span data-ttu-id="62a28-168">作業系統錯誤。備份至 URL 時收到來自遠端端點的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="62a28-168">Operating system error Backup to URL received an exception from the remote endpoint.</span></span> <span data-ttu-id="62a28-169">例外狀況訊息: 無法讀取傳輸連線的資料: 此連接已經關閉。</span><span class="sxs-lookup"><span data-stu-id="62a28-169">Exception Message: Unable to read data from the transport connection: The connection was closed.</span></span>  
  
 <span data-ttu-id="62a28-170">如果您使用追蹤旗標 3051 開啟詳細資訊記錄，可能也會在記錄檔中看到下列資訊：</span><span class="sxs-lookup"><span data-stu-id="62a28-170">If you turn on the verbose logging using the trace flag 3051 you may also see the following message in the logs:</span></span>  
  
 <span data-ttu-id="62a28-171">HTTP 狀態碼 502，HTTP 狀態訊息 Proxy 錯誤 (每分鐘 HTTP 要求數目超過設定的限制。</span><span class="sxs-lookup"><span data-stu-id="62a28-171">HTTP status code 502, HTTP Status Message Proxy Error ( The number of HTTP requests per minute exceeded the configured limit.</span></span> <span data-ttu-id="62a28-172">請連絡您的 ISA Server 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="62a28-172">Contact your ISA Server administrator.</span></span>  <span data-ttu-id="62a28-173">)</span><span class="sxs-lookup"><span data-stu-id="62a28-173">)</span></span>  
  
 <span data-ttu-id="62a28-174">**預設 Proxy 設定未收取：**</span><span class="sxs-lookup"><span data-stu-id="62a28-174">**Default Proxy Settings not picked up:**</span></span>  
  
 <span data-ttu-id="62a28-175">有時不會收取預設設定，導致 proxy 驗證錯誤，如下所示：檔案 \*"" 上發生無法容錯的 i/o 錯誤 http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: 。備份至 URL 時收到來自遠端端點的例外狀況。例外狀況訊息：遠端伺服器傳回錯誤： (407) \* **需要 Proxy 驗證**。</span><span class="sxs-lookup"><span data-stu-id="62a28-175">Sometimes the default settings are not picked up causing proxy authentication errors such as the one shown below:*A nonrecoverable I/O error occurred on file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (407)* **Proxy Authentication Required**.</span></span>  
  
 <span data-ttu-id="62a28-176">若要解決這個問題，使用下列步驟建立組態檔，讓備份至 URL 處理序可以使用預設 Proxy 設定：</span><span class="sxs-lookup"><span data-stu-id="62a28-176">To resolve this issue, create a configuration file that allows the Backup to URL process to use the default proxy settings using the following steps:</span></span>  
  
1.  <span data-ttu-id="62a28-177">建立具有下列 xml 的組態檔，名稱為 BackuptoURL.exe.config：</span><span class="sxs-lookup"><span data-stu-id="62a28-177">Create a configuration file named BackuptoURL.exe.config  with the following xml:</span></span>  
  
    ```  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
  
    ```  
  
2.  <span data-ttu-id="62a28-178">將組態檔放在 SQL Server 執行個體的 Binn 資料夾。</span><span class="sxs-lookup"><span data-stu-id="62a28-178">Place the configuration file in the Binn folder of the SQL Server Instance.</span></span> <span data-ttu-id="62a28-179">例如，如果我的 SQL Server 安裝在電腦的 C 磁片磁碟機上，請將設定檔放在此處： *C:\Program FILES\MICROSOFT SQL Server\MSSQL12. \<InstanceName>\MSSQL\Binn*。</span><span class="sxs-lookup"><span data-stu-id="62a28-179">For example, if my SQL Server is installed on the C drive of the machine, place the configuration file here: *C:\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\Binn*.</span></span>  
  
## <a name="troubleshooting-sql-server-managed-backup-to-azure"></a><span data-ttu-id="62a28-180">SQL Server Managed Backup 到 Azure 的疑難排解</span><span class="sxs-lookup"><span data-stu-id="62a28-180">Troubleshooting SQL Server Managed Backup to Azure</span></span>  
 <span data-ttu-id="62a28-181">因為 SQL Server Managed Backup 會建置在「備份至 URL」之上，所以稍早章節所述的疑難排解提示適用於使用 SQL Server Managed Backup 的資料庫或執行個體。</span><span class="sxs-lookup"><span data-stu-id="62a28-181">Since SQL Server Managed Backup is built on top of Backup to URL, the troubleshooting tips described in the earlier sections apply to databases or instances using SQL Server Managed Backup.</span></span>  <span data-ttu-id="62a28-182">針對[SQL Server 受控備份至 azure](sql-server-managed-backup-to-microsoft-azure.md)中的疑難排解，會詳細說明針對 SQL Server 受控備份至 azure 進行疑難排解的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="62a28-182">Information about troubleshooting SQL Server Managed Backup to Azure is described in detail in [Troubleshooting SQL Server Managed  Backup to Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62a28-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62a28-183">See Also</span></span>  
 [<span data-ttu-id="62a28-184">從儲存在 Azure 中的備份還原</span><span class="sxs-lookup"><span data-stu-id="62a28-184">Restoring From Backups Stored in Azure</span></span>](restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
