---
title: 第 9 課： 從 Azure 儲存體還原資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5e7c2350bb2a9b1f8c31da8e094459b5bc8ccd90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606283"
---
# <a name="lesson-9-restore-a-database-from-azure-storage"></a><span data-ttu-id="2f90b-103">第 9 課：</span><span class="sxs-lookup"><span data-stu-id="2f90b-103">Lesson 9.</span></span> <span data-ttu-id="2f90b-104">從 Azure 儲存體還原資料庫</span><span class="sxs-lookup"><span data-stu-id="2f90b-104">Restore a database from Azure Storage</span></span>
  <span data-ttu-id="2f90b-105">在這一課，您將瞭解如何將資料庫備份檔案從 Azure 儲存體還原到資料庫，此資料庫位於內部部署或 Azure 中的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="2f90b-105">In this lesson, you will learn how to restore a database backup file from Azure Storage to a database, which either resides on-premises or in a virtual machine in Azure.</span></span> <span data-ttu-id="2f90b-106">進行這一課並不需要完成第 4、5、6、7 和 8 課。</span><span class="sxs-lookup"><span data-stu-id="2f90b-106">To follow this lesson, you do not need to complete Lesson 4, 5, 6, 7, and 8.</span></span>  
  
 <span data-ttu-id="2f90b-107">這個課程假設您已完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2f90b-107">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="2f90b-108">您已在來源電腦上建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f90b-108">You have created a database in the source machine.</span></span>  
  
-   <span data-ttu-id="2f90b-109">您已使用 [ [SQL Server 備份和還原與 Azure Blob 儲存體服務](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)] 功能，在 Azure 儲存體中建立資料庫 ( .bak) 的備份。</span><span class="sxs-lookup"><span data-stu-id="2f90b-109">You have created a backup of your database (.bak) in Azure Storage by using the [SQL Server Backup and Restore with Azure Blob Storage Service](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) feature.</span></span> <span data-ttu-id="2f90b-110">請注意，您將需要在這個步驟中建立另一個 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="2f90b-110">Note that you will need to create another SQL Server Credential in this step.</span></span> <span data-ttu-id="2f90b-111">這個認證會使用儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f90b-111">This credential uses storage account keys.</span></span>  
  
-   <span data-ttu-id="2f90b-112">您有 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="2f90b-112">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="2f90b-113">您已在 Azure 儲存體帳戶底下建立容器。</span><span class="sxs-lookup"><span data-stu-id="2f90b-113">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="2f90b-114">您已在容器上建立具有讀取、寫入和列出權限的原則。</span><span class="sxs-lookup"><span data-stu-id="2f90b-114">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="2f90b-115">您也已經產生 SAS 金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f90b-115">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="2f90b-116">您已在電腦上建立 SQL Server 認證，以 Azure 儲存體整合功能。</span><span class="sxs-lookup"><span data-stu-id="2f90b-116">You have created a SQL Server credential on your machine for Azure Storage Integration feature.</span></span> <span data-ttu-id="2f90b-117">請注意，這個認證需要共用存取簽章 (SAS) 金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f90b-117">Note that this credential requires a Shared Access Signature (SAS) key.</span></span>  
  
 <span data-ttu-id="2f90b-118">若要從 Azure 儲存體還原資料庫，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="2f90b-118">To restore a database from Azure Storage, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="2f90b-119">啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="2f90b-119">Start SQL Server Management Studio.</span></span> <span data-ttu-id="2f90b-120">連接到預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="2f90b-120">Connect to the default instance.</span></span>  
  
2.  <span data-ttu-id="2f90b-121">按一下 [標準] 工具列上的 [追加**查詢**]。</span><span class="sxs-lookup"><span data-stu-id="2f90b-121">Click **New Query** on the Standard Toolbar.</span></span>  
  
3.  <span data-ttu-id="2f90b-122">將下列完整指令碼複製並貼入查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="2f90b-122">Copy and paste the following complete script to the query window.</span></span> <span data-ttu-id="2f90b-123">視需要修改腳本。</span><span class="sxs-lookup"><span data-stu-id="2f90b-123">Modify the script as needed.</span></span>  
  
     <span data-ttu-id="2f90b-124">**注意：** 您會執行 `RESTORE` 語句，將 Azure 儲存體中的資料庫 ( 備份還原至另一部電腦中的資料庫實例) 。</span><span class="sxs-lookup"><span data-stu-id="2f90b-124">**Note:** You run the `RESTORE` statement to restore the database backup (.bak) in Azure Storage to a database instance in another machine.</span></span>  
  
    ```sql  
  
    USE master   
    GO   
    -- Create a new database to be backed up.   
    CREATE DATABASE TestDbRestoreFrom;   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    SELECT * from dbo.Table1;   
    GO   
    -- Create a credential to be used by SQL Server Backup and Restore with Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Azure Storage.   
    BACKUP DATABASE TestDBRestoreFrom    
    TO URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
          WITH CREDENTIAL = 'BackupCredential'    
         ,COMPRESSION   
         ,STATS = 5;   
    GO    
    -- Create a Shared Access Signature credential   
    CREATE CREDENTIAL [https://teststorageaccnt.blob.core.windows.net/testrestorefrom]   
    WITH IDENTITY='SHARED ACCESS SIGNATURE',   
    SECRET = 'sv=2012-02-12&sr=c&si=policy_resfrom&sig=EhVpzLUXjG4ThAMLmVhrnoiCt8IfmD3BsuYiMawGzxc%3D'   
    GO   
    USE master;   
    GO   
    RESTORE DATABASE TestDBRestoreFrom    
    FROM URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
    WITH    
    CREDENTIAL = 'BackupCredential',    
    REPLACE,   
    MOVE 'TestDBRestoreFrom' TO 'C:\Backup\TestDBRestoreFrom.mdf',     
    MOVE 'TestDBRestoreFrom_log' TO 'C:\Backup\TestDBRestoreFrom_log.ldf';   
    GO  
  
    ```  
  
 <span data-ttu-id="2f90b-125">**教學課程結束：在 Azure 儲存體服務中 SQL Server 資料檔案**</span><span class="sxs-lookup"><span data-stu-id="2f90b-125">**End of Tutorial: SQL Server Data Files in Azure Storage service**</span></span>  
  
  
