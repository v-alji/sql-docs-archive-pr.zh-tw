---
title: SQL Server 備份至 URL | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6918a099e00b1de9e773320b5c6c0e4089859e02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703026"
---
# <a name="sql-server-backup-to-url"></a><span data-ttu-id="2dd8c-102">SQL Server 備份至 URL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-102">SQL Server Backup to URL</span></span>
  <span data-ttu-id="2dd8c-103">本主題將介紹使用 Azure Blob 儲存體服務作為備份目的地所需的概念、需求和元件。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-103">This topic introduces the concepts, requirements and components necessary to use the Azure Blob storage service as a backup destination.</span></span> <span data-ttu-id="2dd8c-104">使用磁碟或磁帶時，備份和還原功能相同或類似，只有些許的差異。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-104">The backup and restore functionality are same or similar to when using DISK or TAPE, with a few differences.</span></span> <span data-ttu-id="2dd8c-105">這些差異在於許多顯而易見的例外狀況，本主題中將內含某些程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-105">The differences are and any notable exceptions, and a few code examples are included in this topic.</span></span>  
  
## <a name="requirements-components-and-concepts"></a><span data-ttu-id="2dd8c-106">需求、元件和概念</span><span class="sxs-lookup"><span data-stu-id="2dd8c-106">Requirements, Components, and Concepts</span></span>  
 <span data-ttu-id="2dd8c-107">**本節內容：**</span><span class="sxs-lookup"><span data-stu-id="2dd8c-107">**In this section:**</span></span>  
  
-   [<span data-ttu-id="2dd8c-108">安全性</span><span class="sxs-lookup"><span data-stu-id="2dd8c-108">Security</span></span>](#security)  
  
-   [<span data-ttu-id="2dd8c-109">重要元件和概念簡介</span><span class="sxs-lookup"><span data-stu-id="2dd8c-109">Introduction to Key Components and Concepts</span></span>](#intorkeyconcepts)  
  
-   [<span data-ttu-id="2dd8c-110">Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="2dd8c-110">Azure Blob Storage Service</span></span>](#Blob)  
  
-   [<span data-ttu-id="2dd8c-111">SQL Server 元件</span><span class="sxs-lookup"><span data-stu-id="2dd8c-111">SQL Server Components</span></span>](#sqlserver)  
  
-   [<span data-ttu-id="2dd8c-112">限制</span><span class="sxs-lookup"><span data-stu-id="2dd8c-112">Limitations</span></span>](#limitations)  
  
-   [<span data-ttu-id="2dd8c-113">支援 Backup/Restore 語句</span><span class="sxs-lookup"><span data-stu-id="2dd8c-113">Support for Backup/Restore Statements</span></span>](#Support)  
  
-   [<span data-ttu-id="2dd8c-114">在 SQL Server Management Studio 中使用備份工作</span><span class="sxs-lookup"><span data-stu-id="2dd8c-114">Using Backup Task in SQL Server Management Studio</span></span>](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   <span data-ttu-id="2dd8c-115">[使用 [維護計畫精靈] 將 SQL Server 備份至 URL](sql-server-backup-to-url.md#MaintenanceWiz)</span><span class="sxs-lookup"><span data-stu-id="2dd8c-115">[SQL Server Backup to URL Using Maintenance Plan Wizard](sql-server-backup-to-url.md#MaintenanceWiz)</span></span>  
  
-   [<span data-ttu-id="2dd8c-116">使用 SQL Server Management Studio 從 Azure 儲存體還原</span><span class="sxs-lookup"><span data-stu-id="2dd8c-116">Restoring from Azure storage Using SQL Server Management Studio</span></span>](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a><a name="security"></a> <span data-ttu-id="2dd8c-117">Security</span><span class="sxs-lookup"><span data-stu-id="2dd8c-117">Security</span></span>  
 <span data-ttu-id="2dd8c-118">以下是備份至 Azure Blob 儲存體服務或從中還原時的安全性考慮和需求。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-118">The following are security considerations and requirements when backing up to or restoring from the Azure Blob storage services.</span></span>  
  
-   <span data-ttu-id="2dd8c-119">建立 Azure Blob 儲存體服務的容器時，建議您將存取權設定為 [**私**用]。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-119">When creating a container for the Azure Blob storage service, we recommend that you set the access to **private**.</span></span> <span data-ttu-id="2dd8c-120">將存取權設定為 [私用] 可限制只有能夠提供必要資訊向 Azure 帳戶驗證的使用者或帳戶，才有存取權。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-120">Setting the access to private restricts the access to users or accounts able to provide the necessary information to authenticate to the Azure account.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2dd8c-121">需要將 Azure 帳戶名稱和存取金鑰驗證儲存在認證中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-121">requires Azure account name and access key authentication to be stored in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential.</span></span> <span data-ttu-id="2dd8c-122">此資訊會在執行備份或還原作業時，用來向 Azure 帳戶進行驗證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-122">This information is used to authenticate to the Azure account when it performs backup or restore operations.</span></span>  
  
-   <span data-ttu-id="2dd8c-123">用來發出 BACKUP 或 RESTORE 命令的使用者帳戶應該位於擁有 **改變任何認證** 權限的 **db_backup 運算子** 資料庫角色中。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-123">The user account that is used to issue BACKUP or RESTORE commands should be in the **db_backup operator** database role with **Alter any credential** permissions.</span></span>  
  
###  <a name="introduction-to-key-components-and-concepts"></a><a name="intorkeyconcepts"></a><span data-ttu-id="2dd8c-124">重要元件和概念簡介</span><span class="sxs-lookup"><span data-stu-id="2dd8c-124">Introduction to Key Components and Concepts</span></span>  
 <span data-ttu-id="2dd8c-125">下列兩節將介紹 Azure Blob 儲存體服務，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份至 Azure blob 儲存體服務或從中還原時使用的元件。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-125">The following two sections introduce the Azure Blob storage service, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components used when backing up to or restoring from the Azure Blob storage service.</span></span> <span data-ttu-id="2dd8c-126">請務必瞭解這些元件，以及它們之間的互動，以執行 Azure Blob 儲存體服務的備份或還原。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-126">It is important to understand the components and the interaction between them to do a backup to or restore from the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="2dd8c-127">建立 Azure 帳戶是此程式的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-127">Creating an Azure account is the first step to this process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2dd8c-128">會使用**Azure 儲存體帳戶名稱**及其**存取金鑰**值來驗證和讀取 blob，並將其寫入儲存體服務。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-128">uses the **Azure storage account name** and its **access key** values to authenticate and write and read blobs to the storage service.</span></span> <span data-ttu-id="2dd8c-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認證會儲存這項驗證資訊，並且在備份或還原作業期間使用。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-129">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential stores this authentication information and is used during the backup or restore operations.</span></span> <span data-ttu-id="2dd8c-130">如需建立儲存體帳戶和執行簡單還原的完整逐步解說，請參閱[使用 Azure 儲存體服務進行 SQL Server 備份和還原的教學](https://go.microsoft.com/fwlink/?LinkId=271615)課程。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-130">For a complete walkthrough of creating a storage account and performing a simple restore, see [Tutorial Using Azure Storage Service for SQL Server Backup and Restore](https://go.microsoft.com/fwlink/?LinkId=271615).</span></span>  
  
 <span data-ttu-id="2dd8c-131">![將儲存體帳戶對應至 SQL 認證](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "將儲存體帳戶對應至 SQL 認證")</span><span class="sxs-lookup"><span data-stu-id="2dd8c-131">![mapping storage account to sql credentials](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping storage account to sql credentials")</span></span>  
  
###  <a name="azure-blob-storage-service"></a><a name="Blob"></a><span data-ttu-id="2dd8c-132">Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="2dd8c-132">Azure Blob Storage Service</span></span>  
 <span data-ttu-id="2dd8c-133">**儲存體帳戶：** 儲存體帳戶是所有儲存體服務的起點。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-133">**Storage Account:** The storage account is the starting point for all storage services.</span></span> <span data-ttu-id="2dd8c-134">若要存取 Azure Blob 儲存體服務，請先建立 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-134">To access the Azure Blob Storage service, first create an Azure storage account.</span></span> <span data-ttu-id="2dd8c-135">必須要有**儲存體帳戶名稱**及其**存取金鑰**屬性，才能向 Azure Blob 儲存體服務及其元件進行驗證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-135">The **storage account name** and its **access key** properties are required to authenticate to the Azure Blob Storage service and its components.</span></span>  
  
 <span data-ttu-id="2dd8c-136">**容器：** 容器提供一組 Blob 的群組，而且可以儲存不限數目的 Blob。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-136">**Container:** A container provides a grouping of a set of Blobs, and can store an unlimited number of Blobs.</span></span> <span data-ttu-id="2dd8c-137">若要將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份寫入 Azure Blob 服務，您至少必須建立根容器。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-137">To write a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to the Azure Blob service, you must have at least the root container created.</span></span>  
  
 <span data-ttu-id="2dd8c-138">**Blob：** 任何類型和大小的檔案。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-138">**Blob:** A file of any type and size.</span></span> <span data-ttu-id="2dd8c-139">有兩種類型的 blob 可儲存在 Azure Blob 儲存體服務中：區塊和分頁 blob。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-139">There are two types of blobs that can be stored in the Azure Blob storage service: block and page blobs.</span></span> <span data-ttu-id="2dd8c-140"> 備份會使用分頁 Blob 做為 Blob 類型。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup uses page Blobs as the Blob type.</span></span> <span data-ttu-id="2dd8c-141">您可以使用下列 URL 格式來定址 blob： HTTPs:// \<storage account> . blob.core.windows.net/\<container>/\<blob></span><span class="sxs-lookup"><span data-stu-id="2dd8c-141">Blobs are addressable using the following URL format: https://\<storage account>.blob.core.windows.net/\<container>/\<blob></span></span>  
  
 <span data-ttu-id="2dd8c-142">![Azure Blob 儲存體](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob 儲存體")</span><span class="sxs-lookup"><span data-stu-id="2dd8c-142">![Azure Blob Storage](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob Storage")</span></span>  
  
 <span data-ttu-id="2dd8c-143">如需有關 Azure Blob 儲存體服務的詳細資訊，請參閱[如何使用 Azure Blob 儲存體服務](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)</span><span class="sxs-lookup"><span data-stu-id="2dd8c-143">For more information about the Azure Blob storage service, see [How to use the Azure Blob Storage Service](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)</span></span>  
  
 <span data-ttu-id="2dd8c-144">如需有關分頁 Blob 的詳細資訊，請參閱 [了解區塊 Blob 和分頁 Blob](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)</span><span class="sxs-lookup"><span data-stu-id="2dd8c-144">For more information about page Blobs, see [Understanding Block and Page Blobs](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)</span></span>  
  
###  <a name="ssnoversion-components"></a><a name="sqlserver"></a> <span data-ttu-id="2dd8c-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件</span><span class="sxs-lookup"><span data-stu-id="2dd8c-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components</span></span>  
 <span data-ttu-id="2dd8c-146">**URL：** URL 會指定唯一備份檔案的統一資源識別項 (URI)。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-146">**URL:** A URL specifies a Uniform Resource Identifier (URI) to a unique backup file.</span></span> <span data-ttu-id="2dd8c-147">此 URL 是用來提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份檔案的位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-147">The URL is used to provide the location and name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup file.</span></span> <span data-ttu-id="2dd8c-148">在此執行中，唯一有效的 URL 是指向 Azure 儲存體帳戶中分頁 Blob 的 URL。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-148">In this implementation, the only valid URL is one that points to a page Blob in an Azure storage account.</span></span> <span data-ttu-id="2dd8c-149">此 URL 必須指向實際的 Blob，而非只有容器。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-149">The URL must point to an actual Blob, not just a container.</span></span> <span data-ttu-id="2dd8c-150">如果 Blob 不存在，就會建立 Blob。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-150">If the Blob does not exist, it is created.</span></span> <span data-ttu-id="2dd8c-151">如果指定了現有的 Blob，除非指定了 "WITH FORMAT" 選項，否則 BACKUP 會失敗。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-151">If an existing Blob is specified, BACKUP fails, unless the "WITH FORMAT" option is specified.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="2dd8c-152">如果您選擇將備份檔案複製並上傳至 Azure Blob 儲存體服務，請使用分頁 Blob 作為儲存體選項。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-152">If you choose to copy and upload a backup file to the Azure Blob storage service, use page blob as your storage option.</span></span> <span data-ttu-id="2dd8c-153">不支援從區塊 Blob 還原。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-153">Restores from Block Blobs are not supported.</span></span> <span data-ttu-id="2dd8c-154">從區塊 Blob 類型進行 RESTORE 會失敗，並出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-154">RESTORE from a block blob type fails with an error.</span></span>  
  
 <span data-ttu-id="2dd8c-155">以下是 URL 值範例： HTTP [s]：//ACCOUNTNAME.Blob.core.windows.net/ \<CONTAINER> / \<FILENAME.bak> 。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-155">Here is a sample URL value: http[s]://ACCOUNTNAME.Blob.core.windows.net/\<CONTAINER>/\<FILENAME.bak>.</span></span> <span data-ttu-id="2dd8c-156">HTTPS 不是必要項目，但是建議使用。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-156">HTTPS is not required, but is recommended.</span></span>  
  
 <span data-ttu-id="2dd8c-157">**認證：** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認證是用來儲存連線到 SQL Server 外部資源所需之驗證資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-157">**Credential:** A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span>  <span data-ttu-id="2dd8c-158">在這裡， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份和還原程式會使用認證來向 Azure Blob 儲存體服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-158">Here, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore processes use credential to authenticate to the Azure Blob storage service.</span></span> <span data-ttu-id="2dd8c-159">認證會儲存儲存體帳戶的名稱以及儲存體帳戶的 **存取金鑰** 值。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-159">The Credential stores the name of the storage account and the storage account **access key** values.</span></span> <span data-ttu-id="2dd8c-160">一旦建立認證之後，您必須在發出 BACKUP/RESTORE 陳述式時，在 WITH CREDENTIAL 選項中指定認證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-160">Once the credential is created, it must be specified in the WITH CREDENTIAL option when issuing the BACKUP/RESTORE statements.</span></span> <span data-ttu-id="2dd8c-161">如需有關如何查看、複製或重新產生儲存體帳戶**存取金鑰**的詳細資訊，請參閱[儲存體帳戶存取金鑰](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-161">For more information about how to view, copy or regenerate storage account **access keys**, see [Storage Account Access Keys](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).</span></span>  
  
 <span data-ttu-id="2dd8c-162">如需有關如何建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認證的逐步指示，請參閱本主題稍後的＜ [建立認證](#credential) ＞範例。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-162">For step by step instructions about how to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential, see [Create a Credential](#credential) example later in this topic.</span></span>  
  
 <span data-ttu-id="2dd8c-163">如需認證的一般資訊，請參閱 [認證](../security/authentication-access/credentials-database-engine.md)</span><span class="sxs-lookup"><span data-stu-id="2dd8c-163">For general information about credentials, see [Credentials](../security/authentication-access/credentials-database-engine.md)</span></span>  
  
 <span data-ttu-id="2dd8c-164">如需使用認證之其他範例的詳細資訊，請參閱[建立 SQL Server Agent Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-164">For information, on other examples where credentials are used, see [Create a SQL Server Agent Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md).</span></span>  
  
###  <a name="limitations"></a><a name="limitations"></a> <span data-ttu-id="2dd8c-165">限制</span><span class="sxs-lookup"><span data-stu-id="2dd8c-165">Limitations</span></span>  
  
-   <span data-ttu-id="2dd8c-166">不支援備份至進階儲存體。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-166">Backup to premium storage is not supported.</span></span>  
  
-   <span data-ttu-id="2dd8c-167">支援的備份大小上限為 1 TB。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-167">The maximum backup size supported is 1 TB.</span></span>  
  
-   <span data-ttu-id="2dd8c-168">您可以使用 TSQL、SMO 或 PowerShell 指令程式發出 Backup 或 Restore 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-168">You can issue backup or restore statements by using TSQL, SMO, or PowerShell cmdlets.</span></span> <span data-ttu-id="2dd8c-169">目前未啟用使用 SQL Server Management Studio 備份或還原嚮導，從 Azure Blob 儲存體服務進行備份或還原。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-169">A backup to or restoring from the Azure Blob storage service by using SQL Server Management Studio Backup or Restore wizard is not currently enabled.</span></span>  
  
-   <span data-ttu-id="2dd8c-170">不支援建立邏輯裝置名稱。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-170">Creating a logical device name is not supported.</span></span> <span data-ttu-id="2dd8c-171">因此，不支援使用 sp_dumpdevice 或透過 SQL Server Management Studio 加入 URL 做為備份裝置。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-171">So adding URL as a backup device using sp_dumpdevice or through SQL Server Management Studio is not supported.</span></span>  
  
-   <span data-ttu-id="2dd8c-172">不支援附加至現有的備份 Blob。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-172">Appending to existing backup blobs is not supported.</span></span> <span data-ttu-id="2dd8c-173">現有 Blob 的備份只能使用 WITH FORMAT 選項來覆寫。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-173">Backups to an existing Blob can only be overwritten by using the WITH FORMAT option.</span></span>  
  
-   <span data-ttu-id="2dd8c-174">不支援在單一備份作業中，備份至多個 Blob。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-174">Backup to multiple blobs in a single backup operation is not supported.</span></span> <span data-ttu-id="2dd8c-175">例如，下列程式碼會傳回錯誤：</span><span class="sxs-lookup"><span data-stu-id="2dd8c-175">For example, the following returns an error:</span></span>  
  
    ```sql
    BACKUP DATABASE AdventureWorks2012
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'
          WITH CREDENTIAL = 'mycredential'
         ,STATS = 5;  
    GO
    ```  
  
-   <span data-ttu-id="2dd8c-176">不支援使用 `BACKUP` 來指定區塊大小。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-176">Specifying a block size with `BACKUP` is not supported.</span></span>  
  
-   <span data-ttu-id="2dd8c-177">不支援指定 `MAXTRANSFERSIZE`。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-177">Specifying `MAXTRANSFERSIZE` is not supported.</span></span>  
  
-   <span data-ttu-id="2dd8c-178">不支援指定備份組選項 - `RETAINDAYS` 和 `EXPIREDATE`。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-178">Specifying backupset options - `RETAINDAYS` and `EXPIREDATE` are not supported.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2dd8c-179">的備份裝置名稱大小上限為 259 個字元。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-179">has a maximum limit of 259 characters for a backup device name.</span></span> <span data-ttu-id="2dd8c-180">BACKUP TO URL 會用 36 個字元的必要項目指定 URL - 'https://.blob.core.windows.net//.bak '，而保留 223 個字元供帳戶、容器和 Blob 名稱共用。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-180">The BACKUP TO URL consumes 36 characters for the required elements used to specify the URL - 'https://.blob.core.windows.net//.bak', leaving 223 characters for account, container, and blob names put together.</span></span>  
  
###  <a name="support-for-backuprestore-statements"></a><a name="Support"></a> <span data-ttu-id="2dd8c-181">支援 Backup/Restore 陳述式</span><span class="sxs-lookup"><span data-stu-id="2dd8c-181">Support for Backup/Restore Statements</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="2dd8c-182">Backup/Restore 陳述式</span><span class="sxs-lookup"><span data-stu-id="2dd8c-182">Backup/Restore Statement</span></span>|<span data-ttu-id="2dd8c-183">支援</span><span class="sxs-lookup"><span data-stu-id="2dd8c-183">Supported</span></span>|<span data-ttu-id="2dd8c-184">例外狀況</span><span class="sxs-lookup"><span data-stu-id="2dd8c-184">Exceptions</span></span>|<span data-ttu-id="2dd8c-185">註解</span><span class="sxs-lookup"><span data-stu-id="2dd8c-185">Comments</span></span>|  
|<span data-ttu-id="2dd8c-186">備份</span><span class="sxs-lookup"><span data-stu-id="2dd8c-186">BACKUP</span></span>|<span data-ttu-id="2dd8c-187">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-187">&#x2713;</span></span>|<span data-ttu-id="2dd8c-188">不支援 BLOCKSIZE 和 MAXTRANSFERSIZE。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-188">BLOCKSIZE, and MAXTRANSFERSIZE are not supported.</span></span>|<span data-ttu-id="2dd8c-189">需要指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-189">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="2dd8c-190">RESTORE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-190">RESTORE</span></span>|<span data-ttu-id="2dd8c-191">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-191">&#x2713;</span></span>||<span data-ttu-id="2dd8c-192">需要指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-192">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="2dd8c-193">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-193">RESTORE FILELISTONLY</span></span>|<span data-ttu-id="2dd8c-194">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-194">&#x2713;</span></span>||<span data-ttu-id="2dd8c-195">需要指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-195">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="2dd8c-196">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-196">RESTORE HEADERONLY</span></span>|<span data-ttu-id="2dd8c-197">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-197">&#x2713;</span></span>||<span data-ttu-id="2dd8c-198">需要指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-198">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="2dd8c-199">RESTORE LABELONLY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-199">RESTORE LABELONLY</span></span>|<span data-ttu-id="2dd8c-200">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-200">&#x2713;</span></span>||<span data-ttu-id="2dd8c-201">需要指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-201">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="2dd8c-202">RESTORE VERIFYONLY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-202">RESTORE VERIFYONLY</span></span>|<span data-ttu-id="2dd8c-203">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-203">&#x2713;</span></span>||<span data-ttu-id="2dd8c-204">需要指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-204">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="2dd8c-205">RESTORE REWINDONLY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-205">RESTORE REWINDONLY</span></span>|<span data-ttu-id="2dd8c-206">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-206">&#x2713;</span></span>|||  
  
 <span data-ttu-id="2dd8c-207">如需 Backup 陳述式的語法和一般資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-207">For syntax and general information about backup statements, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
 <span data-ttu-id="2dd8c-208">如需 Restore 陳述式的語法和一般資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-208">For syntax and general information about restore statements, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
### <a name="support-for-backup-arguments"></a><span data-ttu-id="2dd8c-209">支援 Backup 引數</span><span class="sxs-lookup"><span data-stu-id="2dd8c-209">Support for Backup Arguments</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="2dd8c-210">引數</span><span class="sxs-lookup"><span data-stu-id="2dd8c-210">Argument</span></span>|<span data-ttu-id="2dd8c-211">支援</span><span class="sxs-lookup"><span data-stu-id="2dd8c-211">Supported</span></span>|<span data-ttu-id="2dd8c-212">例外狀況</span><span class="sxs-lookup"><span data-stu-id="2dd8c-212">Exception</span></span>|<span data-ttu-id="2dd8c-213">註解</span><span class="sxs-lookup"><span data-stu-id="2dd8c-213">Comments</span></span>|  
|<span data-ttu-id="2dd8c-214">DATABASE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-214">DATABASE</span></span>|<span data-ttu-id="2dd8c-215">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-215">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-216">記錄</span><span class="sxs-lookup"><span data-stu-id="2dd8c-216">LOG</span></span>|<span data-ttu-id="2dd8c-217">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-217">&#x2713;</span></span>|||  
||  
|<span data-ttu-id="2dd8c-218">TO (URL)</span><span class="sxs-lookup"><span data-stu-id="2dd8c-218">TO (URL)</span></span>|<span data-ttu-id="2dd8c-219">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-219">&#x2713;</span></span>|<span data-ttu-id="2dd8c-220">與 DISK 和 TAPE 不同，URL 不支援指定或建立邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-220">Unlike DISK and TAPE, URL does not support specifying or creating a logical name.</span></span>|<span data-ttu-id="2dd8c-221">這個引數是用來指定備份檔案的 URL 路徑。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-221">This argument is used to specify the URL path for the backup file.</span></span>|  
|<span data-ttu-id="2dd8c-222">MIRROR TO</span><span class="sxs-lookup"><span data-stu-id="2dd8c-222">MIRROR TO</span></span>|<span data-ttu-id="2dd8c-223">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-223">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-224">**WITH 選項：**</span><span class="sxs-lookup"><span data-stu-id="2dd8c-224">**WITH OPTIONS:**</span></span>||||  
|<span data-ttu-id="2dd8c-225">CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-225">CREDENTIAL</span></span>|<span data-ttu-id="2dd8c-226">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-226">&#x2713;</span></span>||<span data-ttu-id="2dd8c-227">只有在使用 BACKUP TO URL 選項備份至 Azure Blob 儲存體服務時，才支援 WITH CREDENTIAL。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-227">WITH CREDENTIAL is only supported when using BACKUP TO URL option to back up to the Azure Blob storage service.</span></span>|  
|<span data-ttu-id="2dd8c-228">DIFFERENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-228">DIFFERENTIAL</span></span>|<span data-ttu-id="2dd8c-229">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-229">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-230">COPY_ONLY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-230">COPY_ONLY</span></span>|<span data-ttu-id="2dd8c-231">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-231">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-232">COMPRESSION&#124;NO_COMPRESSION</span><span class="sxs-lookup"><span data-stu-id="2dd8c-232">COMPRESSION&#124;NO_COMPRESSION</span></span>|<span data-ttu-id="2dd8c-233">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-233">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-234">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2dd8c-234">DESCRIPTION</span></span>|<span data-ttu-id="2dd8c-235">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-235">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-236">NAME</span><span class="sxs-lookup"><span data-stu-id="2dd8c-236">NAME</span></span>|<span data-ttu-id="2dd8c-237">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-237">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-238">EXPIREDATE &#124; RETAINDAYS</span><span class="sxs-lookup"><span data-stu-id="2dd8c-238">EXPIREDATE &#124; RETAINDAYS</span></span>|<span data-ttu-id="2dd8c-239">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-239">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-240">NOINIT &#124; INIT</span><span class="sxs-lookup"><span data-stu-id="2dd8c-240">NOINIT &#124; INIT</span></span>|<span data-ttu-id="2dd8c-241">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-241">&#x2713;</span></span>||<span data-ttu-id="2dd8c-242">如果使用這個選項，則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-242">This option is ignored if used.</span></span><br /><br /> <span data-ttu-id="2dd8c-243">您無法附加至 Blob。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-243">Appending to blobs is not possible.</span></span> <span data-ttu-id="2dd8c-244">若要覆寫備份，請使用 FORMAT 引數。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-244">To overwrite a backup use the FORMAT argument.</span></span>|  
|<span data-ttu-id="2dd8c-245">NOSKIP &#124; SKIP</span><span class="sxs-lookup"><span data-stu-id="2dd8c-245">NOSKIP &#124; SKIP</span></span>|<span data-ttu-id="2dd8c-246">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-246">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-247">NOFORMAT &#124; FORMAT</span><span class="sxs-lookup"><span data-stu-id="2dd8c-247">NOFORMAT &#124; FORMAT</span></span>|<span data-ttu-id="2dd8c-248">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-248">&#x2713;</span></span>||<span data-ttu-id="2dd8c-249">如果使用這個選項，則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-249">This option is ignored if used.</span></span><br /><br /> <span data-ttu-id="2dd8c-250">除非指定了 WITH FORMAT，否則帶入現有 Blob 的備份會失敗。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-250">A backup taken to an existing blob fails unless WITH FORMAT is specified.</span></span> <span data-ttu-id="2dd8c-251">指定 WITH FORMAT 時，系統會覆寫現有的 Blob。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-251">The existing blob is overwritten when WITH FORMAT is specified.</span></span>|  
|<span data-ttu-id="2dd8c-252">MEDIADESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2dd8c-252">MEDIADESCRIPTION</span></span>|<span data-ttu-id="2dd8c-253">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-253">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-254">MEDIANAME</span><span class="sxs-lookup"><span data-stu-id="2dd8c-254">MEDIANAME</span></span>|<span data-ttu-id="2dd8c-255">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-255">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-256">BLOCKSIZE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-256">BLOCKSIZE</span></span>|<span data-ttu-id="2dd8c-257">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-257">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-258">BUFFERCOUNT</span><span class="sxs-lookup"><span data-stu-id="2dd8c-258">BUFFERCOUNT</span></span>|<span data-ttu-id="2dd8c-259">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-259">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-260">MAXTRANSFERSIZE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-260">MAXTRANSFERSIZE</span></span>|<span data-ttu-id="2dd8c-261">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-261">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-262">NO_CHECKSUM &#124; CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="2dd8c-262">NO_CHECKSUM &#124; CHECKSUM</span></span>|<span data-ttu-id="2dd8c-263">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-263">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-264">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="2dd8c-264">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="2dd8c-265">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-265">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-266">STATS</span><span class="sxs-lookup"><span data-stu-id="2dd8c-266">STATS</span></span>|<span data-ttu-id="2dd8c-267">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-267">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-268">REWIND &#124; NOREWIND</span><span class="sxs-lookup"><span data-stu-id="2dd8c-268">REWIND &#124; NOREWIND</span></span>|<span data-ttu-id="2dd8c-269">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-269">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-270">UNLOAD &#124; NOUNLOAD</span><span class="sxs-lookup"><span data-stu-id="2dd8c-270">UNLOAD &#124; NOUNLOAD</span></span>|<span data-ttu-id="2dd8c-271">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-271">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-272">NORECOVERY &#124; STANDBY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-272">NORECOVERY &#124; STANDBY</span></span>|<span data-ttu-id="2dd8c-273">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-273">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-274">NO_TRUNCATE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-274">NO_TRUNCATE</span></span>|<span data-ttu-id="2dd8c-275">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-275">&#x2713;</span></span>|||  
  
 <span data-ttu-id="2dd8c-276">如需 Backup 引數的詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-276">For more information about backup arguments, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
### <a name="support-for-restore-arguments"></a><span data-ttu-id="2dd8c-277">支援 Restore 引數</span><span class="sxs-lookup"><span data-stu-id="2dd8c-277">Support for Restore Arguments</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="2dd8c-278">引數</span><span class="sxs-lookup"><span data-stu-id="2dd8c-278">Argument</span></span>|<span data-ttu-id="2dd8c-279">支援</span><span class="sxs-lookup"><span data-stu-id="2dd8c-279">Supported</span></span>|<span data-ttu-id="2dd8c-280">例外狀況</span><span class="sxs-lookup"><span data-stu-id="2dd8c-280">Exceptions</span></span>|<span data-ttu-id="2dd8c-281">註解</span><span class="sxs-lookup"><span data-stu-id="2dd8c-281">Comments</span></span>|  
|<span data-ttu-id="2dd8c-282">DATABASE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-282">DATABASE</span></span>|<span data-ttu-id="2dd8c-283">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-283">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-284">記錄</span><span class="sxs-lookup"><span data-stu-id="2dd8c-284">LOG</span></span>|<span data-ttu-id="2dd8c-285">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-285">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-286">FROM (URL)</span><span class="sxs-lookup"><span data-stu-id="2dd8c-286">FROM (URL)</span></span>|<span data-ttu-id="2dd8c-287">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-287">&#x2713;</span></span>||<span data-ttu-id="2dd8c-288">FROM URL 引數是用來指定備份檔案的 URL 路徑。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-288">The FROM URL argument is used to specify the URL path for the backup file.</span></span>|  
|<span data-ttu-id="2dd8c-289">**WITH Options:**</span><span class="sxs-lookup"><span data-stu-id="2dd8c-289">**WITH Options:**</span></span>||||  
|<span data-ttu-id="2dd8c-290">CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-290">CREDENTIAL</span></span>|<span data-ttu-id="2dd8c-291">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-291">&#x2713;</span></span>||<span data-ttu-id="2dd8c-292">只有在使用 [從 URL 還原] 選項從 Azure Blob 儲存體服務還原時，才支援 WITH CREDENTIAL。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-292">WITH CREDENTIAL is only supported when using RESTORE FROM URL option to restore from Azure Blob Storage service.</span></span>|  
|<span data-ttu-id="2dd8c-293">PARTIAL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-293">PARTIAL</span></span>|<span data-ttu-id="2dd8c-294">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-294">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-295">RECOVERY &#124; NORECOVERY &#124; STANDBY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-295">RECOVERY &#124; NORECOVERY &#124; STANDBY</span></span>|<span data-ttu-id="2dd8c-296">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-296">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-297">LOADHISTORY</span><span class="sxs-lookup"><span data-stu-id="2dd8c-297">LOADHISTORY</span></span>|<span data-ttu-id="2dd8c-298">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-298">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-299">MOVE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-299">MOVE</span></span>|<span data-ttu-id="2dd8c-300">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-300">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-301">REPLACE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-301">REPLACE</span></span>|<span data-ttu-id="2dd8c-302">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-302">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-303">RESTART</span><span class="sxs-lookup"><span data-stu-id="2dd8c-303">RESTART</span></span>|<span data-ttu-id="2dd8c-304">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-304">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-305">RESTRICTED_USER</span><span class="sxs-lookup"><span data-stu-id="2dd8c-305">RESTRICTED_USER</span></span>|<span data-ttu-id="2dd8c-306">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-306">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-307">FILE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-307">FILE</span></span>|<span data-ttu-id="2dd8c-308">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-308">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-309">PASSWORD</span><span class="sxs-lookup"><span data-stu-id="2dd8c-309">PASSWORD</span></span>|<span data-ttu-id="2dd8c-310">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-310">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-311">MEDIANAME</span><span class="sxs-lookup"><span data-stu-id="2dd8c-311">MEDIANAME</span></span>|<span data-ttu-id="2dd8c-312">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-312">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-313">MEDIAPASSWORD</span><span class="sxs-lookup"><span data-stu-id="2dd8c-313">MEDIAPASSWORD</span></span>|<span data-ttu-id="2dd8c-314">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-314">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-315">BLOCKSIZE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-315">BLOCKSIZE</span></span>|<span data-ttu-id="2dd8c-316">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-316">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-317">BUFFERCOUNT</span><span class="sxs-lookup"><span data-stu-id="2dd8c-317">BUFFERCOUNT</span></span>|<span data-ttu-id="2dd8c-318">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-318">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-319">MAXTRANSFERSIZE</span><span class="sxs-lookup"><span data-stu-id="2dd8c-319">MAXTRANSFERSIZE</span></span>|<span data-ttu-id="2dd8c-320">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-320">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-321">CHECKSUM &#124; NO_CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="2dd8c-321">CHECKSUM &#124; NO_CHECKSUM</span></span>|<span data-ttu-id="2dd8c-322">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-322">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-323">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="2dd8c-323">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="2dd8c-324">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-324">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-325">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="2dd8c-325">FILESTREAM</span></span>|<span data-ttu-id="2dd8c-326">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-326">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-327">STATS</span><span class="sxs-lookup"><span data-stu-id="2dd8c-327">STATS</span></span>|<span data-ttu-id="2dd8c-328">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-328">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-329">REWIND &#124; NOREWIND</span><span class="sxs-lookup"><span data-stu-id="2dd8c-329">REWIND &#124; NOREWIND</span></span>|<span data-ttu-id="2dd8c-330">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-330">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-331">UNLOAD &#124; NOUNLOAD</span><span class="sxs-lookup"><span data-stu-id="2dd8c-331">UNLOAD &#124; NOUNLOAD</span></span>|<span data-ttu-id="2dd8c-332">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-332">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-333">KEEP_REPLICATION</span><span class="sxs-lookup"><span data-stu-id="2dd8c-333">KEEP_REPLICATION</span></span>|<span data-ttu-id="2dd8c-334">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-334">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-335">KEEP_CDC</span><span class="sxs-lookup"><span data-stu-id="2dd8c-335">KEEP_CDC</span></span>|<span data-ttu-id="2dd8c-336">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-336">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-337">ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER</span><span class="sxs-lookup"><span data-stu-id="2dd8c-337">ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER</span></span>|<span data-ttu-id="2dd8c-338">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-338">&#x2713;</span></span>|||  
|<span data-ttu-id="2dd8c-339">STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK</span><span class="sxs-lookup"><span data-stu-id="2dd8c-339">STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK</span></span>|<span data-ttu-id="2dd8c-340">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-340">&#x2713;</span></span>|||  
  
 <span data-ttu-id="2dd8c-341">如需 Restore 引數的詳細資訊，請參閱 [RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-341">For more information about Restore arguments, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
##  <a name="using-backup-task-in-sql-server-management-studio"></a><a name="BackupTaskSSMS"></a><span data-ttu-id="2dd8c-342">在 SQL Server Management Studio 中使用備份工作</span><span class="sxs-lookup"><span data-stu-id="2dd8c-342">Using Backup Task in SQL Server Management Studio</span></span>  
 <span data-ttu-id="2dd8c-343">SQL Server Management Studio 中的備份工作已增強為包含 URL 做為其中一個目的地選項，以及備份至 Azure 儲存體（例如 SQL 認證）所需的其他支持對象。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-343">The Backup task in SQL Server Management Studio has been enhanced to include URL as one of the destination options, and other supporting objects required to backup to Azure storage like the SQL Credential.</span></span>  
  
 <span data-ttu-id="2dd8c-344">下列步驟說明對備份資料庫工作所做的變更，以允許備份至 Azure 儲存體。：</span><span class="sxs-lookup"><span data-stu-id="2dd8c-344">The following steps describe the changes made to the Back Up Database task to allow for backing up to Azure storage.:</span></span>  
  
1.  <span data-ttu-id="2dd8c-345">啟動 SQL Server Management Studio 並連接至 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-345">Start SQL Server Management Studio and connect to the SQL Server instance.</span></span>  <span data-ttu-id="2dd8c-346">選取您要備份的資料庫，並在 [工作]**上按一下**滑鼠右鍵，然後選取 [**備份 ...**]。這會開啟 [備份資料庫] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-346">Select a database you want to backup, and right click on **Tasks**, and select **Back Up..**. This opens the Back Up Database dialog box.</span></span>  
  
2.  <span data-ttu-id="2dd8c-347">在 [一般] 頁面上，[ **URL** ] 選項是用來建立 Azure 儲存體的備份。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-347">On the general page the **URL** option is used to create a backup to Azure storage.</span></span> <span data-ttu-id="2dd8c-348">當您選取此選項時，會在此頁面上看到其他啟用的選項：</span><span class="sxs-lookup"><span data-stu-id="2dd8c-348">When you select this option, you see other options enabled on this page:</span></span>  
  
    1.  <span data-ttu-id="2dd8c-349">**檔案名稱：** 備份檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-349">**File Name:** Name of the backup file.</span></span>  
  
    2.  <span data-ttu-id="2dd8c-350">**SQL 認證：** 您可以指定現有的 SQL Server 認證，或按一下 [SQL 認證] 方塊旁的 [**建立**] 來建立新的認證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-350">**SQL Credential:** You can either specify an existing SQL Server Credential, or can create a new one by clicking on the **Create** next to the SQL Credential box.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="2dd8c-351">在您按一下 **[建立]** 時開啟的對話方塊需要管理憑證或訂閱的發行設定檔。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-351">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="2dd8c-352">SQL Server 目前支援發行設定檔 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-352">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="2dd8c-353">若要下載發行設定檔的支援版本，請參閱＜ [下載發行設定檔 2.0](https://go.microsoft.com/fwlink/?LinkId=396421)＞。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-353">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
        >   
        >  <span data-ttu-id="2dd8c-354">如果您無法存取管理憑證或發行設定檔，可以使用 Transact-SQL 或 SQL Server Management Studio 來指定儲存體帳戶名稱和存取金鑰資訊，藉以建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-354">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="2dd8c-355">請參閱[建立認證](#credential)一節中的範例程式碼，以使用 transact-sql 來建立認證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-355">See the sample code in the [Create a Credential](#credential) section to create a credential using Transact-SQL.</span></span> <span data-ttu-id="2dd8c-356">或者，使用 SQL Server Management Studio，在資料庫引擎執行個體中，以滑鼠右鍵按一下 **[安全性]**、選取 **[新增]**，然後選取 **[認證]**。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-356">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="2dd8c-357">針對 **[識別]** 指定儲存體帳戶名稱，並且在 **[密碼]** 欄位中指定存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-357">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
    3.  <span data-ttu-id="2dd8c-358">**Azure 儲存體容器：** 用來儲存備份檔案的 Azure 儲存體容器名稱。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-358">**Azure storage container:** The name of the Azure storage container to store the backup files.</span></span>  
  
    4.  <span data-ttu-id="2dd8c-359">**URL 前置詞：** 這會利用上述步驟中說明欄位內所指定的資訊，自動建立。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-359">**URL prefix:** This is built automatically using the information specified in the fields described in the previous steps.</span></span> <span data-ttu-id="2dd8c-360">如果您手動編輯此值，請確定其與您先前提供的其他資訊相符。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-360">If you do edit this value manually, make sure it matches with the other information you provided previously.</span></span> <span data-ttu-id="2dd8c-361">例如，如果您修改了儲存體 URL，請確定 SQL 認證已設定為對相同的儲存體帳戶進行驗證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-361">For example if you modify the storage URL, make sure the SQL Credential is set to authenticate to the same storage account.</span></span>  
  
 <span data-ttu-id="2dd8c-362">當您選取 **URL** 作為目的地時，[媒體選項] 頁面中的某些選項會停用。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-362">When you select URL as the destination, certain options in the **Media Options** page are disabled.</span></span>  <span data-ttu-id="2dd8c-363">下列主題包含有關備份資料庫對話方塊的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="2dd8c-363">The following topics have more information on the Back Up Database dialog:</span></span>  
  
 [<span data-ttu-id="2dd8c-364">備份資料庫 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-364">Back Up Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [<span data-ttu-id="2dd8c-365">備份資料庫 &#40;媒體選項頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-365">Back Up Database &#40;Media Options Page&#41;</span></span>](back-up-database-media-options-page.md)  
  
 [<span data-ttu-id="2dd8c-366">備份資料庫 &#40;備份選項頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-366">Back Up Database &#40;Backup Options Page&#41;</span></span>](back-up-database-backup-options-page.md)  
  
 [<span data-ttu-id="2dd8c-367">建立認證 - 向 Azure 儲存體驗證</span><span class="sxs-lookup"><span data-stu-id="2dd8c-367">Create Credential - Authenticate to Azure Storage</span></span>](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="sql-server-backup-to-url-using-maintenance-plan-wizard"></a><a name="MaintenanceWiz"></a><span data-ttu-id="2dd8c-368">使用維護計畫 Wizard SQL Server 備份至 URL</span><span class="sxs-lookup"><span data-stu-id="2dd8c-368">SQL Server Backup to URL Using Maintenance Plan Wizard</span></span>  
 <span data-ttu-id="2dd8c-369">與先前所述的備份工作類似，SQL Server Management Studio 中的維護計畫 Wizard 已增強為包含**URL**作為其中一個目的地選項，以及備份至 Azure 儲存體（例如 SQL 認證）所需的其他支持對象。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-369">Similar to the backup task described previously, the Maintenance Plan Wizard in SQL Server Management Studio has been enhanced to include **URL** as one of the destination options, and other supporting objects required to backup to Azure storage like the SQL Credential.</span></span> <span data-ttu-id="2dd8c-370">如需詳細資訊，請參閱＜ **Using Maintenance Plan Wizard** ＞中的＜ [定義備份工作](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure)＞一節。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-370">For more information, see  the **Define Backup Tasks** section in [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).</span></span>  
  
##  <a name="restoring-from-azure-storage-using-sql-server-management-studio"></a><a name="RestoreSSMS"></a><span data-ttu-id="2dd8c-371">使用 SQL Server Management Studio 從 Azure 儲存體還原</span><span class="sxs-lookup"><span data-stu-id="2dd8c-371">Restoring from Azure storage Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2dd8c-372">如果您要還原資料庫，會內含 **[URL]** 做為還原裝置的來源。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-372">If you are restoring a database, **URL** is included as the device to restore from.</span></span> <span data-ttu-id="2dd8c-373">下列步驟說明還原工作中的變更，以允許從 Azure 儲存體進行還原：</span><span class="sxs-lookup"><span data-stu-id="2dd8c-373">Following steps describe the changes in the Restore task to allow restoring from Azure storage:</span></span>  
  
1.  <span data-ttu-id="2dd8c-374">當您在 SQL Server Management Studio 的還原工作之 [一般] \*\*\*\* 頁面中選取 [裝置] \*\*\*\* 時，會連結到內含 **URL** 作為備份媒體類型的 [選取備份裝置] \*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-374">When you select **Devices** in the **General** page of the Restore task in SQL Server Management Studio, this takes you to the **Select backup devices** dialog box which includes **URL** as a backup media type.</span></span>  
  
2.  <span data-ttu-id="2dd8c-375">當您選取 **[URL]** 並按一下 **[新增]** 時，會開啟 **[連接到 Azure 儲存體]** 對話。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-375">When you select **URL** and click **Add**, this opens the **Connect to Azure storage** dialog.</span></span> <span data-ttu-id="2dd8c-376">指定要向 Azure 儲存體驗證的 SQL 認證資訊。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-376">Specify the SQL Credential information to authenticate to Azure storage.</span></span>  
  
3.  <span data-ttu-id="2dd8c-377">SQL Server 接著會使用您提供的 SQL 認證資訊連接到 Azure 儲存體，並開啟 [**在 Azure 中尋找備份檔案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-377">SQL Server then connects to Azure storage using the SQL Credential information you provided and opens the **Locate Backup File in Azure** dialog.</span></span> <span data-ttu-id="2dd8c-378">位於儲存體中的備份檔案，會顯示在此頁面上。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-378">The backup files residing in the storage are displayed on this page.</span></span> <span data-ttu-id="2dd8c-379">選取您要用以還原的檔案，並按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-379">Select the file you want to use to restore and click **OK**.</span></span> <span data-ttu-id="2dd8c-380">這會讓您回到 [**選取備份裝置**] 對話方塊，然後按一下此對話方塊上的 **[確定**]，會帶您回到主要的 [**還原**] 對話方塊，讓您能夠完成還原。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-380">This takes you back to the **Select Backup Devices** dialog, and Clicking **OK** on this dialog takes you back to the main **Restore** dialog where you will be able complete the restore.</span></span>  <span data-ttu-id="2dd8c-381">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="2dd8c-381">For more information see, the following topics:</span></span>  
  
     [<span data-ttu-id="2dd8c-382">還原資料庫 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-382">Restore Database &#40;General Page&#41;</span></span>](restore-database-general-page.md)  
  
     [<span data-ttu-id="2dd8c-383">還原資料庫 &#40;檔案頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-383">Restore Database &#40;Files Page&#41;</span></span>](restore-database-files-page.md)  
  
     [<span data-ttu-id="2dd8c-384">還原資料庫 &#40;選項頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-384">Restore Database &#40;Options Page&#41;</span></span>](restore-database-options-page.md)  
  
##  <a name="code-examples"></a><a name="Examples"></a> <span data-ttu-id="2dd8c-385">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="2dd8c-385">Code Examples</span></span>  
 <span data-ttu-id="2dd8c-386">本節包含下列範例。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-386">This section contains the following examples.</span></span>  
  
-   [<span data-ttu-id="2dd8c-387">建立認證</span><span class="sxs-lookup"><span data-stu-id="2dd8c-387">Create a Credential</span></span>](#credential)  
  
-   [<span data-ttu-id="2dd8c-388">備份完整資料庫</span><span class="sxs-lookup"><span data-stu-id="2dd8c-388">Backing up a complete database</span></span>](#complete)  
  
-   [<span data-ttu-id="2dd8c-389">備份資料庫和記錄</span><span class="sxs-lookup"><span data-stu-id="2dd8c-389">Backing up the database and log</span></span>](#databaselog)  
  
-   [<span data-ttu-id="2dd8c-390">建立主要檔案群組的完整檔案備份</span><span class="sxs-lookup"><span data-stu-id="2dd8c-390">Creating a full file backup of the primary filegroup</span></span>](#filebackup)  
  
-   [<span data-ttu-id="2dd8c-391">建立主要檔案群組的差異檔案備份</span><span class="sxs-lookup"><span data-stu-id="2dd8c-391">Creating a differential file backup of the primary filegroups</span></span>](#differential)  
  
-   [<span data-ttu-id="2dd8c-392">還原資料庫和移動檔案</span><span class="sxs-lookup"><span data-stu-id="2dd8c-392">Restoring a database and move files</span></span>](#restoredbwithmove)  
  
-   [<span data-ttu-id="2dd8c-393">使用 STOPAT 還原至時間點</span><span class="sxs-lookup"><span data-stu-id="2dd8c-393">Restoring to a point-in-time using STOPAT</span></span>](#PITR)  
  
###  <a name="create-a-credential"></a><a name="credential"></a> <span data-ttu-id="2dd8c-394">建立認證</span><span class="sxs-lookup"><span data-stu-id="2dd8c-394">Create a Credential</span></span>  
 <span data-ttu-id="2dd8c-395">下列範例會建立儲存 Azure 儲存體驗證資訊的認證。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-395">The following example creates a credential that stores the Azure Storage authentication information.</span></span>  

   ```sql
   IF NOT EXISTS  
   (SELECT * FROM sys.credentials   
   WHERE credential_identity = 'mycredential')  
   CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
   ,SECRET = '<storage access key>' ;  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
   string secret = "<storage access key>";  
  
   // Create a Credential  
   string credentialName = "mycredential";  
   Credential credential = new Credential(server, credentialName);  
   credential.Create(identity, secret);  
   ```  
  
   ```powershell
   # create variables  
   $storageAccount = "mystorageaccount"  
   $storageKey = "<storage access key>"  
   $secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
   $credentialName = "mycredential"  
  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Create a credential  
   New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString
   ```  
  
###  <a name="backing-up-a-complete-database"></a><a name="complete"></a><span data-ttu-id="2dd8c-396">備份完整資料庫</span><span class="sxs-lookup"><span data-stu-id="2dd8c-396">Backing up a complete database</span></span>  
 <span data-ttu-id="2dd8c-397">下列範例會將 AdventureWorks2012 資料庫備份至 Azure Blob 儲存體服務。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-397">The following example backs up the AdventureWorks2012 database to the Azure Blob storage service.</span></span>
  
   ```sql
   BACKUP DATABASE AdventureWorks2012   
   TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
         WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
   GO
   ```  
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server);  
   ```
  
   ```powershell
   # create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"   
   # for default instance, the $srvpath varilable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance  
   CD $srvPath   
   $backupFile = $backupUrlContainer + "AdventureWorks2012" +  ".bak"  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On
   ```  
  
###  <a name="backing-up-the-database-and-log"></a><a name="databaselog"></a><span data-ttu-id="2dd8c-398">備份資料庫和記錄檔</span><span class="sxs-lookup"><span data-stu-id="2dd8c-398">Backing up the database and log</span></span>  
 <span data-ttu-id="2dd8c-399">下列範例會備份 AdventureWorks2012 範例資料庫，依預設採用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-399">The following example backups up the AdventureWorks2012 sample database, which uses the simple recovery model by default.</span></span> <span data-ttu-id="2dd8c-400">為了支援記錄備份，AdventureWorks2012 資料庫會修改成使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-400">To support log backups, the AdventureWorks2012 database is modified to use the full recovery model.</span></span> <span data-ttu-id="2dd8c-401">然後，此範例會建立 Azure Blob 的完整資料庫備份，並且在更新活動一段時間之後，備份記錄。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-401">The example then creates a full database backup to Azure Blob, and after a period of update activity, backs up the log.</span></span> <span data-ttu-id="2dd8c-402">這個範例會建立含有日期時間戳記的備份檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-402">This example creates a backup file name with a datetime stamp.</span></span>  
  
   ```sql
   -- To permit log backups, before the full database backup, modify the database   
   -- to use the full recovery model.  
   USE master;  
   GO  
   ALTER DATABASE AdventureWorks2012  
      SET RECOVERY FULL;  
   GO  
  
   -- Back up the full AdventureWorks2012 database.  
          -- First create a file name for the backup file with DateTime stamp  
  
   DECLARE @Full_Filename AS VARCHAR (300);  
   SET @Full_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Full_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.bak';   
   --Back up Adventureworks2012 database  
  
   BACKUP DATABASE AdventureWorks2012  
   TO URL =  @Full_Filename  
   WITH CREDENTIAL = 'mycredential';  
   ,COMPRESSION  
   GO  
   -- Back up the AdventureWorks2012 log.  
   DECLARE @Log_Filename AS VARCHAR (300);  
   SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
   BACKUP LOG AdventureWorks2012  
    TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url for data backup  
   string urlDataBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Data-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Database to Url  
   Backup backupData = new Backup();  
   backupData.CredentialName = credentialName;  
   backupData.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backupData.Devices.AddDevice(urlDataBackup, DeviceType.Url);  
   backupData.SqlBackup(server);  
  
   // Generate Unique Url for data backup  
   string urlLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Log-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Database Log to Url  
   Backup backupLog = new Backup();  
   backupLog.CredentialName = credentialName;  
   backupLog.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backupLog.Devices.AddDevice(urlLogBackup, DeviceType.Url);  
   backupLog.Action = BackupActionType.Log;  
   backupLog.SqlBackup(server);  
   ```  

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to theSQL Server Instance
   CD $srvPath   
   #Create a unique file name for the full database backup  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   #Backup Database to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Database    
  
   #Create a unique file name for log backup  
  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup Log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Log
   ```  
  
###  <a name="creating-a-full-file-backup-of-the-primary-filegroup"></a><a name="filebackup"></a><span data-ttu-id="2dd8c-403">建立主要檔案群組的完整檔案備份</span><span class="sxs-lookup"><span data-stu-id="2dd8c-403">Creating a full file backup of the primary filegroup</span></span>  
 <span data-ttu-id="2dd8c-404">下列範例會建立主要檔案群組的完整檔案備份。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-404">The following example creates a full file backup of the primary filegroup.</span></span>
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bck",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Action = BackupActionType.Files;  
   backup.DatabaseFileGroups.Add("PRIMARY");  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server);
   ```
  
   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to the SQL Server Instance  
  
   CD $srvPath   
   #Create a unique file name for the file backup  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bck"  
  
   #Backup Primary File Group to URL  
  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary
   ```  
  
###  <a name="creating-a-differential-file-backup-of-the-primary-filegroup"></a><a name="differential"></a><span data-ttu-id="2dd8c-405">建立主要檔案群組的差異檔案備份</span><span class="sxs-lookup"><span data-stu-id="2dd8c-405">Creating a differential file backup of the primary filegroup</span></span>  
 <span data-ttu-id="2dd8c-406">下列範例會建立主要檔案群組的差異檔案備份。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-406">The following example creates a differential file backup of the primary filegroup.</span></span>  
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012filesdiff.bck'  
       WITH   
          CREDENTIAL = 'mycredential'  
          ,COMPRESSION  
      ,DIFFERENTIAL;  
   GO
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Action = BackupActionType.Files;  
   backup.DatabaseFileGroups.Add("PRIMARY");  
   backup.Incremental = true;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server); 
   ```

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   #Create a differential backup of the primary filegroup
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary -Incremental
   ```  
  
###  <a name="restore-a-database-and-move-files"></a><a name="restoredbwithmove"></a><span data-ttu-id="2dd8c-407">還原資料庫和移動檔案</span><span class="sxs-lookup"><span data-stu-id="2dd8c-407">Restore a database and move files</span></span>  
 <span data-ttu-id="2dd8c-408">若要還原完整資料庫備份並將還原的資料庫移至 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data 目錄，請使用下列步驟。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-408">To restore a full database backup and move the restored database to C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data directory, use the following steps.</span></span>
  
   ```sql
   -- Backup the tail of the log first
   DECLARE @Log_Filename AS VARCHAR (300);  
   SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
   BACKUP LOG AdventureWorks2012  
    TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,NORECOVERY;  
   GO  
  
   RESTORE DATABASE AdventureWorks2012 FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'  
   WITH CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,MOVE 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,STATS = 5
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   backup.SqlBackup(server);  
  
   // Generate Unique Url for tail log backup  
   string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Tail Log to Url  
   Backup backupTailLog = new Backup();  
   backupTailLog.CredentialName = credentialName;  
   backupTailLog.Database = dbName;  
   backupTailLog.Action = BackupActionType.Log;  
   backupTailLog.NoRecovery = true;  
   backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
   backupTailLog.SqlBackup(server);  
  
   // Restore a database and move files  
   string newDataFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
   string newLogFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
   Restore restore = new Restore();  
   restore.CredentialName = credentialName;  
   restore.Database = dbName;  
   restore.ReplaceDatabase = true;  
   restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
   restore.RelocateFiles.Add(new RelocateFile(dbName+ "_Log", newLogFilePath));  
   restore.SqlRestore(server);
   ```  

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTNACENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   # Full database backup to URL  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On      
  
   #Create a unique file name for the tail log backup  
   $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup tail log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery    
  
   # Restore Database and move files
   $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
   $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath)
   ```  
  
###  <a name="restoring-to-a-point-in-time-using-stopat"></a><a name="PITR"></a> <span data-ttu-id="2dd8c-409">使用 STOPAT 還原至時間點</span><span class="sxs-lookup"><span data-stu-id="2dd8c-409">Restoring to a point-in-time using STOPAT</span></span>  
 <span data-ttu-id="2dd8c-410">下列範例會將資料庫還原至某個時間點的狀態，並且顯示還原作業。</span><span class="sxs-lookup"><span data-stu-id="2dd8c-410">The following example restores a database to its state to a point in time, and shows a restore operation.</span></span>  
  
   ```sql
   RESTORE DATABASE AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
   WITH   
     CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,Move 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,NORECOVERY  
    --,REPLACE  
    ,STATS = 5;  
   GO   
  
   RESTORE LOG AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.trn'   
   WITH CREDENTIAL = 'mycredential'  
    ,RECOVERY   
    ,STOPAT = 'Oct 23, 2012 5:00 PM'   
   GO  
   ```  
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   backup.SqlBackup(server);  
  
   // Generate Unique Url for Tail Log backup  
   string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Tail Log to Url  
   Backup backupTailLog = new Backup();  
   backupTailLog.CredentialName = credentialName;  
   backupTailLog.Database = dbName;  
   backupTailLog.Action = BackupActionType.Log;  
   backupTailLog.NoRecovery = true;  
   backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
   backupTailLog.SqlBackup(server);  
  
   // Restore a database and move files  
   string newDataFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
   string newLogFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
   Restore restore = new Restore();  
   restore.CredentialName = credentialName;  
   restore.Database = dbName;  
   restore.ReplaceDatabase = true;  
   restore.NoRecovery = true;  
   restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
   restore.RelocateFiles.Add(new RelocateFile(dbName + "_Log", newLogFilePath));  
   restore.SqlRestore(server);  
      
   // Restore transaction Log with stop at   
   Restore restoreLog = new Restore();  
   restoreLog.CredentialName = credentialName;  
   restoreLog.Database = dbName;  
   restoreLog.Action = RestoreActionType.Log;  
   restoreLog.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restoreLog.ToPointInTime = DateTime.Now.ToString();   
   restoreLog.SqlRestore(server);
   ```
  
   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Navigate to SQL Server Instance Directory
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   # Full database backup to URL  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On     
  
   #Create a unique file name for the tail log backup  
   $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup tail log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery     
  
   # Restore Database and move files
   $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
   $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath) -NoRecovery    
  
   # Restore Transaction log with Stop At:  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backuplogFile  -ToPointInTime (Get-Date).ToString()
   ```  
  
## <a name="see-also"></a><span data-ttu-id="2dd8c-411">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dd8c-411">See Also</span></span>  
 <span data-ttu-id="2dd8c-412">[SQL Server 備份至 URL 的最佳作法和疑難排解](sql-server-backup-to-url-best-practices-and-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="2dd8c-412">[SQL Server Backup to URL Best Practices and Troubleshooting](sql-server-backup-to-url-best-practices-and-troubleshooting.md) </span></span>  
 [<span data-ttu-id="2dd8c-413">系統資料庫的備份與還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2dd8c-413">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](back-up-and-restore-of-system-databases-sql-server.md)   
