---
title: 使用 PowerShell 將多個資料庫備份至 Azure Blob 儲存體服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: f7008339-e69d-4e20-9265-d649da670460
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95da5d0009f88943029e62960e7429b292242bbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596740"
---
# <a name="use-powershell-to-backup-multiple-databases-to-azure-blob-storage-service"></a><span data-ttu-id="56875-102">使用 PowerShell 將多個資料庫備份到 Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="56875-102">Use PowerShell to Backup Multiple Databases to Azure Blob Storage Service</span></span>
  <span data-ttu-id="56875-103">本主題提供範例指令碼，可讓您使用 PowerShell Cmdlet，自動執行 Azure Blob 儲存體服務的備份作業。</span><span class="sxs-lookup"><span data-stu-id="56875-103">This topic provides sample scripts that can be used to automate backups to Azure Blob storage service using PowerShell cmdlets.</span></span>  
  
## <a name="overview-of-powershell-cmdlets-for-backup-and-restore"></a><span data-ttu-id="56875-104">備份與還原之 PowerShell 指令程式的概觀</span><span class="sxs-lookup"><span data-stu-id="56875-104">Overview of PowerShell cmdlets for Backup and Restore</span></span>  
 <span data-ttu-id="56875-105">`Backup-SqlDatabase` 和 `Restore-SqlDatabase` 是進行備份和還原作業所能使用的兩個主要指令程式。</span><span class="sxs-lookup"><span data-stu-id="56875-105">The `Backup-SqlDatabase` and `Restore-SqlDatabase` are the two main cmdlets available to do backup and restore operations.</span></span> <span data-ttu-id="56875-106">此外，自動操作 Azure Blob 儲存體備份作業可能還需要其他 Cmdlet，例如 **SqlCredential** Cmdlet。以下是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 所提供可用於備份及還原之 PowerShell Cmdlet 的清單︰</span><span class="sxs-lookup"><span data-stu-id="56875-106">In addition, there are other cmdlets that may be required to automate backups to Azure Blob storage like the set of **SqlCredential** cmdlets  Following is a list of PowerShell cmdlets available in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that are used in backup and restore operations:</span></span>  
  
 <span data-ttu-id="56875-107">Backup-SqlDatabase</span><span class="sxs-lookup"><span data-stu-id="56875-107">Backup-SqlDatabase</span></span>  
 <span data-ttu-id="56875-108">此指令程式可用於建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份。</span><span class="sxs-lookup"><span data-stu-id="56875-108">This cmdlet is used to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Backup.</span></span>  
  
 <span data-ttu-id="56875-109">Restore-SqlDatabase</span><span class="sxs-lookup"><span data-stu-id="56875-109">Restore-SqlDatabase</span></span>  
 <span data-ttu-id="56875-110">可用於還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="56875-110">Used to restore a database.</span></span>  
  
 <span data-ttu-id="56875-111">New-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="56875-111">New-SqlCredential</span></span>  
 <span data-ttu-id="56875-112">此 Cmdlet 可用於建立 SQL Server 備份至 Azure 儲存體時所使用的 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="56875-112">This cmdlet is used to create a SQL Credential to use for SQL Server Backup to Azure Storage.</span></span> <span data-ttu-id="56875-113">如需有關認證及其在 SQL Server 備份和還原中之用法的詳細資訊，請參閱[使用 Azure Blob 儲存體服務 SQL Server 備份和還原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="56875-113">For more information on credentials and their use in SQL Server Backup and Restore, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="56875-114">Get-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="56875-114">Get-SqlCredential</span></span>  
 <span data-ttu-id="56875-115">此指令程式可用於擷取認證物件及其屬性。</span><span class="sxs-lookup"><span data-stu-id="56875-115">This cmdlet is used to retrieve the Credential object and its properties.</span></span>  
  
 <span data-ttu-id="56875-116">Remove-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="56875-116">Remove-SqlCredential</span></span>  
 <span data-ttu-id="56875-117">刪除 SQL 認證物件</span><span class="sxs-lookup"><span data-stu-id="56875-117">Delete a SQL Credential object</span></span>  
  
 <span data-ttu-id="56875-118">Set-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="56875-118">Set-SqlCredential</span></span>  
 <span data-ttu-id="56875-119">此指令程式可用於變更或設定 SQL 認證物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="56875-119">This cmdlet is used to change or set the properties of the SQL Credential Object.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="56875-120">Credential Cmdlet 是用於備份及還原至 Azure Blob 儲存體的情節。</span><span class="sxs-lookup"><span data-stu-id="56875-120">The Credential cmdlets are used in Backup and Restore to Azure Blob storage scenarios.</span></span>  
  
### <a name="powershell-for-multi-database-multi-instance-backup-operations"></a><span data-ttu-id="56875-121">多個資料庫的 PowerShell，多個執行個體的備份作業</span><span class="sxs-lookup"><span data-stu-id="56875-121">PowerShell for Multi-Database, Multi-Instance Backup Operations</span></span>  
 <span data-ttu-id="56875-122">下列各節包含多種作業的指令碼，例如建立多個 SQL Server 執行個體的 SQL 認證、備份 SQL Server 執行個體中的所有使用者資料庫等等。</span><span class="sxs-lookup"><span data-stu-id="56875-122">The following sections include scripts for various operations like creating a SQL Credential on multiple instance of SQL Server, backing up all user databases in an instance of SQL Server, and such.</span></span> <span data-ttu-id="56875-123">您可以根據環境的需求，利用這些指令碼自動化或排程備份作業。</span><span class="sxs-lookup"><span data-stu-id="56875-123">You can use these scripts to automate or schedule backup operations according to the requirements of your environment.</span></span> <span data-ttu-id="56875-124">此處所提供的指令碼僅為範例，您可以針對您的環境的需要而修改或擴充。</span><span class="sxs-lookup"><span data-stu-id="56875-124">The scripts provided here are examples, and may be modified or extended for your environment.</span></span>  
  
 <span data-ttu-id="56875-125">以下是範例指令碼的注意事項︰</span><span class="sxs-lookup"><span data-stu-id="56875-125">The following are considerations for the sample scripts:</span></span>  
  
1.  <span data-ttu-id="56875-126">**導覽 SQL Server PowerShell 路徑︰** Windows PowerShell 會執行指令程式，以導覽代表 PowerShell 提供者所支援之物件階層的路徑結構。</span><span class="sxs-lookup"><span data-stu-id="56875-126">**Navigating SQL Server PowerShell paths:** Windows PowerShell implements cmdlets to navigate the path structure that represents the hierarchy of objects supported by a PowerShell provider.</span></span> <span data-ttu-id="56875-127">在您導覽至路徑中的節點時，可以使用其他 Cmdlet 來執行目前物件的基本作業。</span><span class="sxs-lookup"><span data-stu-id="56875-127">When you have navigated to a node in the path, you can use other cmdlets to perform basic operations on the current object.</span></span>  
  
2.  <span data-ttu-id="56875-128">`Get-ChildItem` 指令程式︰`Get-ChildItem` 傳回的資訊內容，視在 SQL Server PowerShell 路徑中的位置而定。</span><span class="sxs-lookup"><span data-stu-id="56875-128">`Get-ChildItem` cmdlet: The information returned by the `Get-ChildItem` depends on the location in a SQL Server PowerShell path.</span></span> <span data-ttu-id="56875-129">例如，如果位置在電腦層級，此指令程式會傳回所有安裝在電腦上的 SQL Server Database Engine 執行個體。</span><span class="sxs-lookup"><span data-stu-id="56875-129">For example, if the location is at the computer level, this cmdlet returns all the SQL Server database engine instances installed on the computer.</span></span> <span data-ttu-id="56875-130">又例如，如果位置在物件層級 (例如資料庫)，此指令程式會傳回資料庫物件的清單。</span><span class="sxs-lookup"><span data-stu-id="56875-130">As another example, if the location is at the object level such as databases, then this cmdlet returns a list of database objects.</span></span>  <span data-ttu-id="56875-131">`Get-ChildItem` 指令程式預設不會傳回任何系統物件。</span><span class="sxs-lookup"><span data-stu-id="56875-131">By default the `Get-ChildItem` cmdlet does not return system objects.</span></span>  <span data-ttu-id="56875-132">使用 -Force 參數即可看到系統物件。</span><span class="sxs-lookup"><span data-stu-id="56875-132">Using the -Force parameter you can see the system objects.</span></span>  
  
     <span data-ttu-id="56875-133">如需詳細資訊，請參閱 [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="56875-133">For more information, see [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md).</span></span>  
  
3.  <span data-ttu-id="56875-134">雖然您可以利用變更變數值，嘗試個別變更每一個程式碼範例，但您還是必須針對 Azure Blob 儲存體服務之備份及還原作業，建立其必要條件：Azure Blob 儲存體帳戶與 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="56875-134">Although each code sample can be tried independently by changing the variable values, creating an Azure Storage Account and a SQL Credential are prerequisites and required for all backup and restore operations to Azure Blob storage service.</span></span>  
  
### <a name="create-a-sql-credential-on-all-the-instances-of-sql-server"></a><span data-ttu-id="56875-135">建立所有 SQL Server 執行個體的 SQL 認證</span><span class="sxs-lookup"><span data-stu-id="56875-135">Create a SQL Credential on All the Instances of SQL Server</span></span>  
 <span data-ttu-id="56875-136">下列兩個範例指令碼都會為電腦上所有的 SQL Server 執行個體上建立 SQL 認證 "mybackupToURL"。</span><span class="sxs-lookup"><span data-stu-id="56875-136">There are two sample scripts, and both create a SQL Credential "mybackupToURL" on all the instances of SQL Server on a computer.</span></span> <span data-ttu-id="56875-137">第一個範例比較簡單而且會建立認證，但不會設陷例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56875-137">The first example creates is simple and creates the credential and does not trap exceptions.</span></span>  <span data-ttu-id="56875-138">例如，如果電腦上的某一個執行個體目前已有同名的認證，此指令碼將會失敗。</span><span class="sxs-lookup"><span data-stu-id="56875-138">For example, if there was already an existing credential with the same name on one of the instances of the computer, the script would fail.</span></span> <span data-ttu-id="56875-139">第二個範例會設陷錯誤，並允許指令碼繼續執行。</span><span class="sxs-lookup"><span data-stu-id="56875-139">The second example traps errors and allows the script to continue.</span></span>  
  
```powershell
import-module sqlps  
  
# create variables  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-ChildItem  
#pipe the instances to new-sqlcredentail cmdlet to create SQL credential  
$instances | New-SqlCredential -Name $credentialName -Identity $storageAccount -Secret $secureString  
```  
  
```powershell
import-module sqlps  
  
# set the parameter values
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-ChildItem  
#loop through instances and create a SQL credential, output any errors  
ForEach ($instance In $instances)  
{  
    Try  
{  
     New-SqlCredential -Name $credentialName -path "SQLServer:\SQL\$($instance.name)" -Identity $storageAccount -Secret $secureString -ea Stop
}  
Catch [Exception]  
    {
            Write-Host "instance - $($instance.name): "$_.Exception.Message
    }
 }
```  
  
### <a name="remove-a-sql-credential-from-all-the-instances-of-sql-server"></a><span data-ttu-id="56875-140">移除所有 SQL Server 執行個體的 SQL 認證</span><span class="sxs-lookup"><span data-stu-id="56875-140">Remove A SQL Credential from All the Instances of SQL Server</span></span>  
 <span data-ttu-id="56875-141">此指令碼可用於移除電腦上所安裝之所有 SQL Server 執行個體的特定認證。</span><span class="sxs-lookup"><span data-stu-id="56875-141">This script can be used to remove a specific credential from all the instances of SQL Server installed on the computer.</span></span> <span data-ttu-id="56875-142">如果指定執行個體的認證物件不存在，將會顯示錯誤訊息，而指令碼將會繼續執行，直到檢查過所有執行個體為止。</span><span class="sxs-lookup"><span data-stu-id="56875-142">If the Credential object does not exist on a specific instance, an error message is displayed, and the script continues until all instances are checked.</span></span>  
  
```powershell
import-module sqlps  
  
cd SQLServer:\SQL\COMPUTERNAME  
$credentialName = "mybackuptoURL"  
  
$instances = Get-ChildItem  
  
ForEach ($instance In $instances)  
   {
    Try  
        {  
            $path = "SQLServer:\SQL\$($instance.name)\credentials\$credentialName"   
            Remove-SqlCredential -Path $path -ea stop   
         }  
         Catch [Exception]  
         {  
            Write-Host $_.Exception.Message
        }
    }  
```  
  
### <a name="full-database-backup-for-all-databases-including-system-databases"></a><span data-ttu-id="56875-143">所有資料庫的完整資料庫備份 (包括系統資料庫)</span><span class="sxs-lookup"><span data-stu-id="56875-143">Full Database Backup for all Databases (INCLUDING SYSTEM DATABASES)</span></span>  
 <span data-ttu-id="56875-144">下列指令碼會為電腦上的所有資料庫建立備份。</span><span class="sxs-lookup"><span data-stu-id="56875-144">The following script creates backups of all databases on the computer.</span></span> <span data-ttu-id="56875-145">這包括使用者資料庫和 **msdb** 系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="56875-145">This includes both user databases and **msdb** system database.</span></span> <span data-ttu-id="56875-146">此指令碼會篩選 **tempdb** 和 **model** 系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="56875-146">The script filters out **tempdb** and **model** system databases.</span></span>  
  
```powershell
import-module sqlps  
# set the parameter values  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-ChildItem
# loop through each instances and backup up all the  databases -filter out tempdb and model databases  
  
 ForEach ($instance In $instances)  
 {  
   $path = "sqlserver:\sql\$($instance.name)\databases"  
   $alldatabases = Get-ChildItem -Force -path $path | Where-Object {$_.name -ne "tempdb" -and $_.name -ne "model"}   
   $alldatabases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On -script   
 }
```  
  
### <a name="full-database-backup-for-all-user-databases"></a><span data-ttu-id="56875-147">所有使用者資料庫的完整資料庫備份</span><span class="sxs-lookup"><span data-stu-id="56875-147">Full Database Backup for ALL User Databases</span></span>  
 <span data-ttu-id="56875-148">下列指令碼可用於備份電腦上所有 SQL Server 執行個體的所有使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="56875-148">The following script can be used to back up all the user databases on all the instances of SQL Server on the computer.</span></span>  
  
```powershell
import-module sqlps
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-ChildItem
# loop through each instances and backup up all the user databases  
 ForEach ($instance In $instances)  
 {  
    $databases = dir "sqlserver:\sql\$($instance.name)\databases"  
    $databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On
 }  
```  
  
### <a name="full-database-backup-for-master-and-msdb-system-databases-on-all-the-instances-of-sql-server"></a><span data-ttu-id="56875-149">所有 SQL Server 執行個體上之 Master 和 MSDB 資料庫 (系統資料庫) 的完整資料庫備份</span><span class="sxs-lookup"><span data-stu-id="56875-149">Full Database Backup for MASTER and MSDB (SYSTEM DATABASES) On All the Instances of SQL Server</span></span>  
 <span data-ttu-id="56875-150">下列指令碼可用於備份電腦上安裝之所有 SQL Server 執行個體的 **master** 和 **msdb** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="56875-150">The following script can be used to back up **master** and **msdb** databases on all the instances of SQL Server installed on the computer.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackupToUrl"  
$sysDbs = "master", "msdb"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
$instances = Get-ChildItem
ForEach ($instance In $instances)  
 {  
      ForEach ($s In $sysdbs)  
     {  
        Backup-SqlDatabase -Database $s -path "sqlserver:\sql\$($instance.name)" -BackupContainer  $backupUrlContainer -SqlCredential $credentialName -Compression On   
}
 } 
```  
  
### <a name="full-database-backup-for-all-user-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="56875-151">SQL Server 執行個體上之所有使用者資料庫的完整資料庫備份</span><span class="sxs-lookup"><span data-stu-id="56875-151">Full Database Backup for All User Databases on an Instance of SQL Server</span></span>  
 <span data-ttu-id="56875-152">下列指令碼可用於只備份具名 SQL Server 執行個體上的使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="56875-152">The following script is used to back up only the user databases available on a named instance of SQL Server.</span></span> <span data-ttu-id="56875-153">只要變更 $srvPath 參數值，電腦上的預設執行個體即可使用相同的指令碼。</span><span class="sxs-lookup"><span data-stu-id="56875-153">The same script can be used for the default instance on the computer by changing the $srvPath parameter value.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME"  # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
  
#retrieves the database objects for a specific instance  
$databases = dir $srvPath\databases  
  
#backup all the user databases  
$databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
```  
  
### <a name="full-database-backup-for-only-system-databases-master-and-msdb-on-an-instance-of-sql-server"></a><span data-ttu-id="56875-154">僅限 SQL Server 執行個體上之系統資料庫 (Master 和 MSDB) 的完整資料庫備份</span><span class="sxs-lookup"><span data-stu-id="56875-154">Full Database Backup for Only System Databases (MASTER AND MSDB) On an Instance of SQL Server</span></span>  
 <span data-ttu-id="56875-155">完整的指令碼可用來備份具名 SQL Server 執行個體的 **master** 和 **msdb** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="56875-155">The full script can be used to back up the **master** and the **msdb** databases on a named instance of SQL Server.</span></span> <span data-ttu-id="56875-156">只要變更 $srvPath 參數值，電腦上的預設執行個體即可使用相同的指令碼。</span><span class="sxs-lookup"><span data-stu-id="56875-156">The same script can be used for the default instance on the computer by changing the $srvpath parameter value.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME" # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#navigate to instance level  
cd $srvPath  
  
$sysDbs = "master", "msdb"  
ForEach ($s In $sysDbs)
{  
Backup-SqlDatabase -Database $s -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
}
```  
  
## <a name="see-also"></a><span data-ttu-id="56875-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56875-157">See Also</span></span>
 <span data-ttu-id="56875-158">[使用 Azure Blob 儲存體服務 SQL Server 備份和還原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) [SQL SERVER 備份至 URL 的最佳作法和疑難排解](sql-server-backup-to-url-best-practices-and-troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="56875-158">[SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) [SQL Server Backup to URL Best Practices and Troubleshooting](sql-server-backup-to-url-best-practices-and-troubleshooting.md)</span></span>  
