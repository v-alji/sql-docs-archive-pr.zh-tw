---
title: 刪除擁有使用中租用的備份 Blob 檔案 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 02aea910589633a5c3ec79e283c757727b4d92cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595138"
---
# <a name="deleting-backup-blob-files-with-active-leases"></a><span data-ttu-id="f93eb-102">刪除擁有使用中租用的備份 Blob 檔案</span><span class="sxs-lookup"><span data-stu-id="f93eb-102">Deleting Backup Blob Files with Active Leases</span></span>
  <span data-ttu-id="f93eb-103">備份至 Azure 儲存體或從中還原時，SQL Server 會取得無限期租用，以鎖定 blob 的獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="f93eb-103">When backing up to or restoring from Azure storage, SQL Server acquires an infinite lease in order to lock exclusive access to the blob.</span></span> <span data-ttu-id="f93eb-104">當備份或還原程序順利完成時，就會釋放租用。</span><span class="sxs-lookup"><span data-stu-id="f93eb-104">When the backup or restore process is successfully completed, the lease is released.</span></span> <span data-ttu-id="f93eb-105">如果備份或還原失敗，備份程序會嘗試清除任何無效的 Blob。</span><span class="sxs-lookup"><span data-stu-id="f93eb-105">If a backup or restore fails, the backup process attempts to clean up any invalid blob.</span></span> <span data-ttu-id="f93eb-106">不過，如果由於過長或持續性網路連線失敗而無法備份，備份程序可能無法存取 Blob，而該 Blob 可能仍然是被遺棄狀態。</span><span class="sxs-lookup"><span data-stu-id="f93eb-106">However, if the backup fails due to prolonged or sustained network connectivity failure, the backup  process may not be able gain access to the blob and the blob may remain orphaned.</span></span> <span data-ttu-id="f93eb-107">這表示，在釋放租用之前，無法寫入或刪除 Blob。</span><span class="sxs-lookup"><span data-stu-id="f93eb-107">This means that the blob cannot be written to or deleted until the lease is released.</span></span> <span data-ttu-id="f93eb-108">此主題描述如何釋放租用及刪除 Blob。</span><span class="sxs-lookup"><span data-stu-id="f93eb-108">This topic describes how to release the lease and deleting the blob..</span></span>  
  
 <span data-ttu-id="f93eb-109">如需租用類型的詳細資訊，請閱讀這篇 [文章](https://go.microsoft.com/fwlink/?LinkId=275664)。</span><span class="sxs-lookup"><span data-stu-id="f93eb-109">For more information on the types of leases, read this [article](https://go.microsoft.com/fwlink/?LinkId=275664).</span></span>  
  
 <span data-ttu-id="f93eb-110">如果備份作業失敗，可能會產生無效的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="f93eb-110">If the backup operation fails, it can result in a backup file that is not valid.</span></span>  <span data-ttu-id="f93eb-111">備份 Blob 檔案可能也擁有使用中租用，導致無法刪除或覆寫此檔案。</span><span class="sxs-lookup"><span data-stu-id="f93eb-111">The backup blob file might also have an active lease, preventing it from being deleted or overwritten.</span></span>  <span data-ttu-id="f93eb-112">若要刪除或覆寫這類 Blob，應該先中斷租用。如果發生備份失敗，我們建議您清除租用並刪除 Blob。</span><span class="sxs-lookup"><span data-stu-id="f93eb-112">In order to delete or overwrite such blobs, the lease should first be broken.If there are backup failures, we recommend that you clean up leases and delete blobs.</span></span> <span data-ttu-id="f93eb-113">您也可以選擇在儲存體管理工作中進行定期清除。</span><span class="sxs-lookup"><span data-stu-id="f93eb-113">You can also choose cleanup periodically as part of storage management tasks.</span></span>  
  
 <span data-ttu-id="f93eb-114">如果發生還原失敗，系統不會封鎖後續還原，因此使用中租用可能不會產生問題。</span><span class="sxs-lookup"><span data-stu-id="f93eb-114">If there is a restore failure, subsequent restores are not blocked, and therefore the active lease may not be an issue.</span></span> <span data-ttu-id="f93eb-115">只有當您必須覆寫或刪除 Blob 時，才需要中斷租用。</span><span class="sxs-lookup"><span data-stu-id="f93eb-115">Breaking the lease is only necessary when you have to overwrite or delete the blob.</span></span>  
  
## <a name="managing-orphaned-blobs"></a><span data-ttu-id="f93eb-116">管理被遺棄的 Blob</span><span class="sxs-lookup"><span data-stu-id="f93eb-116">Managing Orphaned Blobs</span></span>  
 <span data-ttu-id="f93eb-117">下列步驟將說明如何在備份或還原活動失敗之後進行清除。</span><span class="sxs-lookup"><span data-stu-id="f93eb-117">The follow steps describe how to clean up after failed backup or restore activity.</span></span> <span data-ttu-id="f93eb-118">所有步驟都可以使用 PowerShell 指令碼來完成。</span><span class="sxs-lookup"><span data-stu-id="f93eb-118">All the steps can be done using PowerShell scripts.</span></span> <span data-ttu-id="f93eb-119">下一節將提供程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="f93eb-119">A code example is provided in the following section:</span></span>  
  
1.  <span data-ttu-id="f93eb-120">**識別擁有租用的 Blob：** 如果您有執行備份程序的指令碼或處理序，就可以在指令碼或處理序內部擷取失敗，並且使用該項資訊來清除 Blob。</span><span class="sxs-lookup"><span data-stu-id="f93eb-120">**Identifying blobs that have leases:** If you have a script or a process that runs the backup processes, you might be able to capture the failure within the script or process and use that to clean up the blobs.</span></span>   <span data-ttu-id="f93eb-121">您也可以使用 LeaseStats 和 LeastState 屬性來識別擁有其租用的 Blob。</span><span class="sxs-lookup"><span data-stu-id="f93eb-121">You can also use the LeaseStats and LeastState properties to identify the blobs that have leases on them.</span></span> <span data-ttu-id="f93eb-122">識別出 Blob 之後，我們建議您檢閱清單、確認備份檔案的有效性，然後再刪除 Blob。</span><span class="sxs-lookup"><span data-stu-id="f93eb-122">Once you have identified the blobs, we recommend that you review the list, verify the validity of the backup file before deleting the blob.</span></span>  
  
2.  <span data-ttu-id="f93eb-123">**中斷租用：** 授權要求可以中斷租用，而不需要提供租用識別碼。</span><span class="sxs-lookup"><span data-stu-id="f93eb-123">**Breaking the lease:** An authorized request can break the lease without supplying a lease ID.</span></span> <span data-ttu-id="f93eb-124">如需詳細資訊，請參閱 [此處](https://go.microsoft.com/fwlink/?LinkID=275664) 。</span><span class="sxs-lookup"><span data-stu-id="f93eb-124">See [here](https://go.microsoft.com/fwlink/?LinkID=275664) for more information.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="f93eb-125">SQL Server 會發出租用識別碼，以便在還原作業期間確立獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="f93eb-125">SQL Server issues a lease ID to establish exclusive access during the restore operation.</span></span> <span data-ttu-id="f93eb-126">還原租用識別碼為 BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2。</span><span class="sxs-lookup"><span data-stu-id="f93eb-126">The restore lease ID is BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.</span></span>  
  
3.  <span data-ttu-id="f93eb-127">**刪除 Blob：** 若要刪除擁有使用中租用的 Blob，您必須先中斷租用。</span><span class="sxs-lookup"><span data-stu-id="f93eb-127">**Deleting the Blob:** To delete a blob that has an active lease, you must first break the lease.</span></span>  
  
###  <a name="powershell-script-example"></a><a name="Code_Example"></a><span data-ttu-id="f93eb-128">PowerShell 腳本範例</span><span class="sxs-lookup"><span data-stu-id="f93eb-128">PowerShell Script Example</span></span>  
 <span data-ttu-id="f93eb-129">\*\* \* \* 重要 \* ： \* \*\*如果您執行的是 PowerShell 2.0，載入 Microsoft WindowsAzure.Storage.dll 元件時可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="f93eb-129">**\*\* Important \*\*** If you are running PowerShell 2.0, you may have problems loading the Microsoft WindowsAzure.Storage.dll assembly.</span></span> <span data-ttu-id="f93eb-130">我們建議您升級為 Powershell 3.0 以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="f93eb-130">We recommend that you upgrade to Powershell 3.0 to solve the issue.</span></span> <span data-ttu-id="f93eb-131">您也可以針對 PowerShell 2.0 使用下列因應措施：</span><span class="sxs-lookup"><span data-stu-id="f93eb-131">You may also use the following workaround for PowerShell 2.0:</span></span>  
  
-   <span data-ttu-id="f93eb-132">使用下列內容來建立或修改 powershell.exe.config 檔案，以便在執行階段載入 .NET 2.0 和 .NET 4.0 組件：</span><span class="sxs-lookup"><span data-stu-id="f93eb-132">Create or modify the powershell.exe.config file to load .NET 2.0 and .NET 4.0 assemblies at runtime with the following:</span></span>  
  
    ```xml
    <?xml version="1.0"?>
    <configuration>
        <startup useLegacyV2RuntimeActivationPolicy="true">
            <supportedRuntime version="v4.0.30319"/>
            <supportedRuntime version="v2.0.50727"/>
        </startup>
    </configuration>
    ```  
  
 <span data-ttu-id="f93eb-133">下列範例將說明如何識別擁有使用中租用的 Blob，然後中斷租用。</span><span class="sxs-lookup"><span data-stu-id="f93eb-133">The following example illustrates identifying blobs that have active leases and then breaking them.</span></span> <span data-ttu-id="f93eb-134">此範例也會示範如何篩選釋放租用識別碼。</span><span class="sxs-lookup"><span data-stu-id="f93eb-134">The example also demonstrates how filter for release lease IDs.</span></span>  
  
 <span data-ttu-id="f93eb-135">執行這個指令碼的秘訣</span><span class="sxs-lookup"><span data-stu-id="f93eb-135">Tips on running this script</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="f93eb-136">如果 Azure Blob 儲存體服務的備份與此腳本同時執行，備份可能會失敗，因為此腳本會中斷備份嘗試同時取得的租用。</span><span class="sxs-lookup"><span data-stu-id="f93eb-136">If a backup to Azure Blob storage service is running at the same time as this script, the backup can fail since this script will break the lease that the backup is trying to acquire at the same time.</span></span> <span data-ttu-id="f93eb-137">建議在維護期間或預期不會執行任何備份時執行這個指令碼。</span><span class="sxs-lookup"><span data-stu-id="f93eb-137">We recommend running this script during a maintenance windows or when no backups are expected to run.</span></span>  
  
1.  <span data-ttu-id="f93eb-138">當您執行此腳本時，系統會提示您提供儲存體帳戶、儲存體金鑰、容器和 Azure 儲存體元件路徑和名稱參數的值。</span><span class="sxs-lookup"><span data-stu-id="f93eb-138">When you run this script, you will be prompted to provide values for the storage account, storage key, container, and the Azure storage assembly path and name parameters.</span></span> <span data-ttu-id="f93eb-139">儲存體的路徑是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f93eb-139">The path of the storage is assembly is the installation directory of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f93eb-140">儲存體組件的檔案名稱是 Microsoft.WindowsAzure.Storage.dll。</span><span class="sxs-lookup"><span data-stu-id="f93eb-140">The file name for the storage assembly is Microsoft.WindowsAzure.Storage.dll.</span></span> <span data-ttu-id="f93eb-141">下面是提示與輸入值的範例：</span><span class="sxs-lookup"><span data-stu-id="f93eb-141">Following is an example of the prompts and values entered:</span></span>  
  
    ```  
    cmdlet  at command pipeline position 1  
    Supply values for the following parameters:  
    storageAccount: mycloudstorageaccount  
    storageKey: 0BopKY7eEha3gBnistYk+904nf  
    blobContainer: mycontainer   
    storageAssemblyPath: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Microsoft.WindowsAzure.Storage.dll  
    ```  
  
2.  <span data-ttu-id="f93eb-142">如果沒有任何鎖定租用的 Blob，您應該會看見下列訊息：</span><span class="sxs-lookup"><span data-stu-id="f93eb-142">If there are no blobs that have locked leases you should see the following message:</span></span>  
  
     <span data-ttu-id="f93eb-143">**沒有任何處於鎖定租用狀態的 Blob**</span><span class="sxs-lookup"><span data-stu-id="f93eb-143">**There are no blobs with locked lease status**</span></span>  
  
     <span data-ttu-id="f93eb-144">如果有鎖定租用的 Blob，您應該會看見下列訊息：</span><span class="sxs-lookup"><span data-stu-id="f93eb-144">If there are blobs with locked leases, you should see the following messages:</span></span>  
  
     <span data-ttu-id="f93eb-145">**中斷租用**</span><span class="sxs-lookup"><span data-stu-id="f93eb-145">**Breaking Leases**</span></span>  
  
     <span data-ttu-id="f93eb-146">**的租用 \<URL of the Blob> 是還原租用：只有當您的 blob 具有仍在使用中的還原租用時，您才會看到此訊息。**</span><span class="sxs-lookup"><span data-stu-id="f93eb-146">**The lease on \<URL of the Blob> is a restore lease: You will see this message only if you have a blob with a restore lease that is still active.**</span></span>  
  
     <span data-ttu-id="f93eb-147">**上的租用 \<URL of the Blob> 不是還原租用中斷租用 \<URL of the Bob> 。**</span><span class="sxs-lookup"><span data-stu-id="f93eb-147">**The lease on \<URL of the Blob> is not a restore lease Breaking lease on \<URL of the Bob>.**</span></span>  
  
```powershell
param(  
       [Parameter(Mandatory=$true)]  
       [string]$storageAccount,  
       [Parameter(Mandatory=$true)]  
       [string]$storageKey,  
       [Parameter(Mandatory=$true)]  
       [string]$blobContainer,  
       [Parameter(Mandatory=$true)]  
       [string]$storageAssemblyPath  
)  
  
# Well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# Load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
#list all the blobs  
$allBlobs = $container.ListBlobs()
  
$lockedBlobs = @()  
# filter blobs that are have Lease Status as "locked"  
foreach($blob in $allBlobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  
  
if ($lockedBlobs.Count -eq 0)  
{
    Write-Host " There are no blobs with locked lease status"  
}

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases"  
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease"  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease"  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)"  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
}
```  
  
## <a name="see-also"></a><span data-ttu-id="f93eb-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f93eb-148">See Also</span></span>  
 [<span data-ttu-id="f93eb-149">SQL Server 備份至 URL 的最佳做法和疑難排解</span><span class="sxs-lookup"><span data-stu-id="f93eb-149">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>](sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
