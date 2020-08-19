---
title: 第 5 課  (選擇性) 使用 TDE 加密您的資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 613b66c04a69364f3c9be1059f95021dd3eff595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597118"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a><span data-ttu-id="afdd1-103">第 5 課</span><span class="sxs-lookup"><span data-stu-id="afdd1-103">Lesson 5.</span></span> <span data-ttu-id="afdd1-104">(選擇性) 使用 TDE 加密資料庫</span><span class="sxs-lookup"><span data-stu-id="afdd1-104">(Optional) Encrypt your database using TDE</span></span>
  <span data-ttu-id="afdd1-105">您可以選擇加密新建立的資料庫。</span><span class="sxs-lookup"><span data-stu-id="afdd1-105">As an optional step, you can encrypt the newly created database.</span></span> <span data-ttu-id="afdd1-106">透明資料加密 (TDE) 會執行資料和記錄檔的即時 I/O 加密和解密。</span><span class="sxs-lookup"><span data-stu-id="afdd1-106">Transparent data encryption (TDE) performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="afdd1-107">這類加密會使用資料庫加密金鑰 (DEK)，該金鑰儲存於資料庫開機記錄中，以便在復原期間可供使用。</span><span class="sxs-lookup"><span data-stu-id="afdd1-107">This kind of encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="afdd1-108">如需詳細資訊，請參閱 [透明資料加密 &#40;TDE&#41;](security/encryption/transparent-data-encryption.md) 並 [將受 TDE 保護的資料庫移至另一個 SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd1-108">For more information, see [Transparent Data Encryption &#40;TDE&#41;](security/encryption/transparent-data-encryption.md) and [Move a TDE Protected Database to Another SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).</span></span>  
  
 <span data-ttu-id="afdd1-109">這個課程假設您已完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="afdd1-109">This lesson assumes you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="afdd1-110">您有 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="afdd1-110">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="afdd1-111">您已在 Azure 儲存體帳戶下建立容器。</span><span class="sxs-lookup"><span data-stu-id="afdd1-111">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="afdd1-112">您已在容器上建立具有讀取、寫入和列出權限的原則。</span><span class="sxs-lookup"><span data-stu-id="afdd1-112">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="afdd1-113">您也已經產生 SAS 金鑰。</span><span class="sxs-lookup"><span data-stu-id="afdd1-113">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="afdd1-114">您已在來源電腦上建立 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="afdd1-114">You have created a SQL Server credential on the source machine.</span></span>  
  
-   <span data-ttu-id="afdd1-115">您已依照第 4 課所述的步驟建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="afdd1-115">You have created a database by following the steps that are described in Lesson 4.</span></span>  
  
 <span data-ttu-id="afdd1-116">如果您想要加密資料庫，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="afdd1-116">If you want to encrypt a database, follow these steps:</span></span>  
  
1.  <span data-ttu-id="afdd1-117">在來源電腦上，於查詢視窗中修改並執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="afdd1-117">In the source machine, modify and run the following statements in a query window:</span></span>  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  <span data-ttu-id="afdd1-118">然後，依照下列步驟加密來源電腦中的新資料庫：</span><span class="sxs-lookup"><span data-stu-id="afdd1-118">Then, encrypt your new database in the source machine by following these steps:</span></span>  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 <span data-ttu-id="afdd1-119">如果您想要了解資料庫的加密狀態及相關聯的資料庫加密金鑰，請執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="afdd1-119">If you want to learn the encryption state of a database and its associated database encryption keys, run the following statement:</span></span>  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 <span data-ttu-id="afdd1-120">如需本課程中使用之 Transact-sql 語句的詳細資訊，請參閱 [建立資料庫 &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)、 [ALTER DATABASE &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql)、 [create MASTER KEY &#40;transact-sql ](/sql/t-sql/statements/create-master-key-transact-sql)&#41;、 [create CERTIFICATE &#40;Transact-sql&#41;](/sql/t-sql/statements/create-certificate-transact-sql)和 [sys. dm_database_encryption_keys &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="afdd1-120">For detailed information the Transact-SQL statements that have been used in this lesson, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql), [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql), and [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).</span></span>  
  
 <span data-ttu-id="afdd1-121">**下一課：**</span><span class="sxs-lookup"><span data-stu-id="afdd1-121">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="afdd1-122">第 6 課：在 Azure 中將資料庫從內部部署來源電腦移轉至目的地電腦</span><span class="sxs-lookup"><span data-stu-id="afdd1-122">Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure</span></span>](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
