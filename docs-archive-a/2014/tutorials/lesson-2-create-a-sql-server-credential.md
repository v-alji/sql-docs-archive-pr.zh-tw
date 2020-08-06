---
title: 第2課：建立 SQL Server 認證 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e8b13c8d4d9e5937064cef5503ec64bfd6e4a2d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710065"
---
# <a name="lesson-2-create-a-sql-server-credential"></a><span data-ttu-id="47458-102">第 2 課：建立 SQL Server 認證</span><span class="sxs-lookup"><span data-stu-id="47458-102">Lesson 2: Create a SQL Server Credential</span></span>
  <span data-ttu-id="47458-103">**認證：** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認證是用來儲存連線到 SQL Server 外部資源所需之驗證資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="47458-103">**Credential:** A [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span>  <span data-ttu-id="47458-104">在這裡， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 備份和還原程式會使用認證來向 Azure Blob 儲存體服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="47458-104">Here, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore processes use credential to authenticate to the Azure Blob storage service.</span></span> <span data-ttu-id="47458-105">認證會儲存儲存體帳戶的名稱以及儲存體帳戶的 **存取金鑰** 值。</span><span class="sxs-lookup"><span data-stu-id="47458-105">The Credential stores the name of the storage account and the storage account **access key** values.</span></span> <span data-ttu-id="47458-106">一旦建立認證之後，您必須在發出 BACKUP/RESTORE 陳述式時，在 WITH CREDENTIAL 選項中指定認證。</span><span class="sxs-lookup"><span data-stu-id="47458-106">Once the credential is created, it must be specified in the WITH CREDENTIAL option when issuing the BACKUP/RESTORE statements.</span></span> <span data-ttu-id="47458-107">如需有關如何查看、複製或重新產生儲存體帳戶**存取金鑰**的詳細資訊，請參閱[儲存體帳戶存取金鑰](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47458-107">For more information about how to view, copy or regenerate storage account **access keys**, see [Storage Account Access Keys](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).</span></span>  
  
 <span data-ttu-id="47458-108">如需認證的一般資訊，請參閱[認證](../relational-databases/security/authentication-access/credentials-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="47458-108">For general information about credentials, see [Credentials](../relational-databases/security/authentication-access/credentials-database-engine.md).</span></span>  
  
 <span data-ttu-id="47458-109">如需使用認證之其他範例的詳細資訊，請參閱[建立 SQL Server Agent Proxy](../ssms/agent/create-a-sql-server-agent-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="47458-109">For information, on other examples where credentials are used, see [Create a SQL Server Agent Proxy](../ssms/agent/create-a-sql-server-agent-proxy.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47458-110">以下所述建立 SQL Server 認證的需求專屬於 SQL Server 備份程式 ([SQL Server 備份至 URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)，以及[SQL Server 受管理的備份至 Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)) 。</span><span class="sxs-lookup"><span data-stu-id="47458-110">The requirements for creating a SQL Server credential described below are specific to SQL Server backup processes ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md), and [SQL Server Managed  Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)).</span></span> <span data-ttu-id="47458-111">SQL Server 在存取 Azure 儲存體以寫入或讀取備份時，會使用儲存體帳戶名稱與存取金鑰資訊。</span><span class="sxs-lookup"><span data-stu-id="47458-111">SQL Server, when accessing Azure storage to write or read backups uses the storage account name and access key information.</span></span>  <span data-ttu-id="47458-112">如需建立認證以在 Azure 儲存體中儲存資料庫檔案的詳細資訊，請參閱 [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)</span><span class="sxs-lookup"><span data-stu-id="47458-112">For more information on creating credentials for storing database files in Azure storage, see [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)</span></span>  
  
## <a name="create-a-sql-server-credential"></a><span data-ttu-id="47458-113">建立 SQL Server 認證</span><span class="sxs-lookup"><span data-stu-id="47458-113">Create a SQL Server Credential</span></span>  
 <span data-ttu-id="47458-114">若要建立 SQL Server 認證，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="47458-114">To create a SQL Server Credential, use the following steps:</span></span>  
  
1.  <span data-ttu-id="47458-115">連接到 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="47458-115">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="47458-116">在 [物件總管] 中，連接到已安裝 AdventureWorks2012 資料庫的 Database Engine 執行個體，或使用您計畫要用於此教學課程的自訂資料庫。</span><span class="sxs-lookup"><span data-stu-id="47458-116">In Object Explorer, connect to the instance of Database Engine that has AdventureWorks2012 database installed, or use your own database you plan to use for this tutorial.</span></span>  
  
3.  <span data-ttu-id="47458-117">在 **[標準]** 工具列上，按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="47458-117">On the **Standard** tool bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="47458-118">將下列範例複製並貼入查詢視窗中，並視需要修改。</span><span class="sxs-lookup"><span data-stu-id="47458-118">Copy and paste the following example into the query window, modify as needed.</span></span>  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     <span data-ttu-id="47458-119">![將儲存體帳戶對應至 SQL 認證](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "將儲存體帳戶對應至 SQL 認證")</span><span class="sxs-lookup"><span data-stu-id="47458-119">![mapping storage account to sql credentials](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping storage account to sql credentials")</span></span>  
  
5.  <span data-ttu-id="47458-120">確認 T-sql 語句，然後按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="47458-120">Verify the T-SQL statement and click **Execute**.</span></span>  
  
 <span data-ttu-id="47458-121">如需有關 Azure Blob 儲存體服務的備份概念和需求的詳細資訊，請參閱[使用 Azure Blob 儲存體服務 SQL Server 備份和還原](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="47458-121">For more information about the Azure Blob storage service for backup concepts and requirements, see [SQL Server Backup and Restore with Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
### <a name="next-lesson"></a><span data-ttu-id="47458-122">下一課</span><span class="sxs-lookup"><span data-stu-id="47458-122">Next Lesson</span></span>  
 <span data-ttu-id="47458-123">[第3課：將完整資料庫備份寫入 Azure Blob 儲存體服務](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="47458-123">[Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).</span></span>  
  
  
