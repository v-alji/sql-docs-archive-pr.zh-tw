---
title: 第3課：建立 SQL Server 認證 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 808438e544e3beb18b2e2afa9c399b5666277483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707522"
---
# <a name="lesson-3-create-a-sql-server-credential"></a><span data-ttu-id="bf6d7-102">第 3 課：建立 SQL Server 認證</span><span class="sxs-lookup"><span data-stu-id="bf6d7-102">Lesson 3: Create a SQL Server Credential</span></span>
  <span data-ttu-id="bf6d7-103">在這一課，您將建立認證，以儲存用來存取 Azure 儲存體帳戶的安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-103">In this lesson, you will create a credential to store security information used to access the Azure storage account.</span></span>  
  
 <span data-ttu-id="bf6d7-104">SQL Server 認證是用來儲存連接到 SQL Server 外部資源所需之驗證資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-104">A SQL Server credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span> <span data-ttu-id="bf6d7-105">認證會儲存儲存體容器的 URI 路徑以及共用存取簽章金鑰值。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-105">The credential stores the URI path of the storage container and the shared access signature key values.</span></span> <span data-ttu-id="bf6d7-106">對於資料或記錄檔所使用的每一個儲存體容器，您必須建立名稱符合容器路徑的 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-106">For each storage container used by a data or log file, you must create a SQL Server Credential whose name matches the container path.</span></span>  
  
 <span data-ttu-id="bf6d7-107">如需認證的一般資訊，請參閱[認證 &#40;資料庫引擎&#41;](security/authentication-access/credentials-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-107">For general information about credentials, see [Credentials &#40;Database Engine&#41;](security/authentication-access/credentials-database-engine.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bf6d7-108">以下所述建立 SQL Server 認證的需求，僅適用于[Azure 功能中 SQL Server 的資料檔案](databases/sql-server-data-files-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-108">The requirements for creating a SQL Server credential described below are specific to the [SQL Server Data Files in Azure](databases/sql-server-data-files-in-microsoft-azure.md) feature.</span></span> <span data-ttu-id="bf6d7-109">如需建立在 Azure 儲存體中執行備份程序所需之認證的資訊，請參閱＜ [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-109">For information on creating credentials for backup processes in Azure storage, see [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
 <span data-ttu-id="bf6d7-110">若要建立 SQL Server 認證，請依照下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="bf6d7-110">To create a SQL Server Credential, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bf6d7-111">連接到 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-111">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="bf6d7-112">在 [物件總管] 中連接到已安裝的 Database Engine 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-112">In Object Explorer, connect to the instance of Database Engine installed.</span></span>  
  
3.  <span data-ttu-id="bf6d7-113">在 [標準] 工具列上，按一下 [新增查詢]。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-113">On the Standard tool bar, click New Query.</span></span>  
  
4.  <span data-ttu-id="bf6d7-114">將下列範例複製並貼入查詢視窗中，並視需要修改。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-114">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="bf6d7-115">下列語句會建立 SQL Server 認證，以儲存儲存體容器的共用存取憑證。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-115">The following statement will create a SQL Server Credential to store your storage container's Shared Access Certificate.</span></span>  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     <span data-ttu-id="bf6d7-116">如需詳細資訊，請參閱 SQL Server 線上叢書中的[&#40;transact-sql&#41;建立認證](/sql/t-sql/statements/create-credential-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-116">For detailed information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) in SQL Server Books Online.</span></span>  
  
5.  <span data-ttu-id="bf6d7-117">若要查看所有可用的認證，可以在查詢視窗中執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="bf6d7-117">To see all available credentials, you can run the following statement in the query window:</span></span>  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     <span data-ttu-id="bf6d7-118">如需有關 sys.databases 的詳細資訊，請參閱 SQL Server 線上叢書中[&#40;transact-sql&#41;的 sys. 認證](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bf6d7-118">For more information on sys.credentials, see [sys.credentials &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="bf6d7-119">**下一課：**</span><span class="sxs-lookup"><span data-stu-id="bf6d7-119">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="bf6d7-120">第 4 課：在 Azure 儲存體中建立資料庫</span><span class="sxs-lookup"><span data-stu-id="bf6d7-120">Lesson 4: Create a database in Azure Storage</span></span>](lesson-3-database-backup-to-url.md)  
  
  
