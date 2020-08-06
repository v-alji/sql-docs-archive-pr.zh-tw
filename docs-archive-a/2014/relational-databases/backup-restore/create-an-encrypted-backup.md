---
title: 建立加密的備份 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d46cc686684d87fe393a5db7cfe01194ae917836
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707634"
---
# <a name="create-an-encrypted-backup"></a><span data-ttu-id="d8acd-102">建立加密的備份</span><span class="sxs-lookup"><span data-stu-id="d8acd-102">Create an Encrypted Backup</span></span>
  <span data-ttu-id="d8acd-103">本主題說明使用 Transact-SQL 建立加密備份所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="d8acd-103">This topic describes the steps necessary to create an encrypted backup using Transact-SQL.</span></span>  
  
## <a name="backup-to-disk-with-encryption"></a><span data-ttu-id="d8acd-104">使用加密備份到磁碟</span><span class="sxs-lookup"><span data-stu-id="d8acd-104">Backup to Disk with Encryption</span></span>  
 <span data-ttu-id="d8acd-105">**必要條件：**</span><span class="sxs-lookup"><span data-stu-id="d8acd-105">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="d8acd-106">必須能夠存取用以建立資料庫備份的本機磁碟或具有足用空間的儲存體。</span><span class="sxs-lookup"><span data-stu-id="d8acd-106">Access to a local disk or to storage with adequate space to create a backup of the database.</span></span>  
  
-   <span data-ttu-id="d8acd-107">主要資料庫的資料庫主要金鑰，以及 SQL Server 執行個體所提供的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8acd-107">A Database Master Key for the master database, and a certificate or asymmetric key available on the instance of SQL Server.</span></span> <span data-ttu-id="d8acd-108">如需加密需求及權限的資訊，請參閱 [備份加密](backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="d8acd-108">For encryption requirements and permissions, see [Backup Encryption](backup-encryption.md).</span></span>  
  
 <span data-ttu-id="d8acd-109">使用下列步驟建立要存放到本機磁碟的資料庫加密備份。</span><span class="sxs-lookup"><span data-stu-id="d8acd-109">Use the following steps to create an encrypted backup of a database to a local disk.</span></span> <span data-ttu-id="d8acd-110">此範例會使用稱為 MyTestDB 的使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="d8acd-110">This example uses a user database called MyTestDB.</span></span>  
  
1.  <span data-ttu-id="d8acd-111">**建立 master 資料庫的資料庫主要金鑰：** 選擇密碼以加密即將儲存於資料庫的主要金鑰副本。</span><span class="sxs-lookup"><span data-stu-id="d8acd-111">**Create a Database Master Key of the master database:** Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span> <span data-ttu-id="d8acd-112">連接到 Database Engine，再啟動新的查詢視窗，將下列範例複製並貼到新的查詢視窗中，然後按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="d8acd-112">Connect to the database engine, start a new query windows and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  <span data-ttu-id="d8acd-113">**建立備份憑證：** 在 master 資料庫中建立備份憑證。</span><span class="sxs-lookup"><span data-stu-id="d8acd-113">**Create a Backup Certificate:** Create a backup certificate in the master database.</span></span> <span data-ttu-id="d8acd-114">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**</span><span class="sxs-lookup"><span data-stu-id="d8acd-114">Copy and paste the following example into the query window and click **Execute**</span></span>  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  <span data-ttu-id="d8acd-115">**備份資料庫：** 指定要使用的加密演算法與憑證。</span><span class="sxs-lookup"><span data-stu-id="d8acd-115">**Backup the database:** Specify the encryption algorithm and certificate to use.</span></span> <span data-ttu-id="d8acd-116">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d8acd-116">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 <span data-ttu-id="d8acd-117">如需加密受 EKM 保護的備份的範例，請參閱[使用 Azure 金鑰保存庫進行可延伸金鑰管理 &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d8acd-117">For an example of encrypting a backup protected by an EKM, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
### <a name="backup-to-azure-storage-with-encryption"></a><span data-ttu-id="d8acd-118">將儲存到 Azure 儲存體的備份加密</span><span class="sxs-lookup"><span data-stu-id="d8acd-118">Backup to Azure Storage with Encryption</span></span>  
 <span data-ttu-id="d8acd-119">如果使用 [SQL Server 備份至 URL]  選項建立要儲存到 Azure 儲存體的備份，其加密步驟完全相同，但您必須使用 URL 作為目的地，並使用 SQL 認證向 Azure 儲存體進行驗證。</span><span class="sxs-lookup"><span data-stu-id="d8acd-119">If you are creating a backup to Azure storage using the **SQL Server Backup to URL** option, the encryption steps are the same, but you must use URL as the destination and a SQL Credential to authenticate to the Azure storage.</span></span> <span data-ttu-id="d8acd-120">如果您想要設定 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 加密選項，請參閱[設定 SQL Server 受管理的備份至 azure](enable-sql-server-managed-backup-to-microsoft-azure.md)和[針對可用性群組設定 SQL Server 受控備份至 azure](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="d8acd-120">If you want to configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] with encryption options, see [Setting up SQL Server Managed Backup to Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) and [Setting up SQL Server Managed Backup to Azure for Availability Groups](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
 <span data-ttu-id="d8acd-121">**必要條件：**</span><span class="sxs-lookup"><span data-stu-id="d8acd-121">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="d8acd-122">一個視窗儲存體帳戶和容器。</span><span class="sxs-lookup"><span data-stu-id="d8acd-122">A windows storage account and a container.</span></span> <span data-ttu-id="d8acd-123">如需詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="d8acd-123">For more information, see.</span></span> <span data-ttu-id="d8acd-124">[第 1 課：建立 Azure 儲存體物件](../../tutorials/lesson-1-create-windows-azure-storage-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="d8acd-124">[Lesson 1: Create Azure Storage Objects](../../tutorials/lesson-1-create-windows-azure-storage-objects.md).</span></span>  
  
-   <span data-ttu-id="d8acd-125">主要資料庫的資料主要金鑰，以及 SQL Server 執行個體的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8acd-125">A Database Master Key for the master database, and a certificate or asymmetric key  on the instance of SQL Server.</span></span> <span data-ttu-id="d8acd-126">如需加密需求及權限的資訊，請參閱 [備份加密](backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="d8acd-126">For encryption requirements and permissions, see [Backup Encryption](backup-encryption.md).</span></span>  
  
1.  <span data-ttu-id="d8acd-127">**建立 SQL Server 認證：** 若要建立 SQL Server 認證，請連線到 Database Engine、開啟新的查詢視窗、複製並貼上下列範例，然後按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="d8acd-127">**Create SQL Server Credential:** To create a SQL Server credential, connect to the Database Engine, open a new query window, and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  <span data-ttu-id="d8acd-128">**建立資料庫主要金鑰：** 選擇密碼以加密即將儲存於資料庫的主要金鑰副本。</span><span class="sxs-lookup"><span data-stu-id="d8acd-128">**Create a Database Master Key:** Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span> <span data-ttu-id="d8acd-129">連接到 Database Engine，再啟動新的查詢視窗，將下列範例複製並貼到新的查詢視窗中，然後按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="d8acd-129">Connect to the database engine, start a new query windows and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  <span data-ttu-id="d8acd-130">**建立備份憑證：** 在 master 資料庫中建立備份憑證。</span><span class="sxs-lookup"><span data-stu-id="d8acd-130">**Create a Backup Certificate:** Create a Backup Certificate in the master database.</span></span> <span data-ttu-id="d8acd-131">複製下列範例，並將其貼到查詢視窗中，然後按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="d8acd-131">Copy and paste the following example in the query window and click **Execute**</span></span>  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  <span data-ttu-id="d8acd-132">**備份資料庫：** 指定要使用的加密演算法與憑證。</span><span class="sxs-lookup"><span data-stu-id="d8acd-132">**Backup the database:** Specify the encryption algorithm and the certificate to use.</span></span> <span data-ttu-id="d8acd-133">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d8acd-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' - this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
