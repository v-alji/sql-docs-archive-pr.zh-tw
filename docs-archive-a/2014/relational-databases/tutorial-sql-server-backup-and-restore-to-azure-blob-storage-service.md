---
title: 教學課程：SQL Server 備份及還原至 Windows Azure Blob 儲存體服務 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
ms.openlocfilehash: d15200968011cdb314829736512f39730782dc0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687742"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a><span data-ttu-id="9c276-102">教學課程：SQL Server 備份及還原至 Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="9c276-102">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>
  <span data-ttu-id="9c276-103">歡迎使用 SQL Server 備份和還原與 Azure Blob 儲存體服務的消費者入門教學課程。</span><span class="sxs-lookup"><span data-stu-id="9c276-103">Welcome to the Getting Started with SQL Server Backup and Restore with Azure Blob Storage Service tutorial.</span></span> <span data-ttu-id="9c276-104">本教學課程可協助您了解如何將備份寫入 Azure Blob 儲存體服務以及從中還原。</span><span class="sxs-lookup"><span data-stu-id="9c276-104">This tutorial helps you understand how to write backups to and restore from the Azure Blob storage service.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="9c276-105">學習內容</span><span class="sxs-lookup"><span data-stu-id="9c276-105">What You Will Learn</span></span>  
 <span data-ttu-id="9c276-106">本教學課程會為您示範如何建立 Windows 儲存體帳戶和 Blob 容器、建立認證以存取儲存體帳戶、將備份寫入 Blob 服務，以及執行簡單還原。</span><span class="sxs-lookup"><span data-stu-id="9c276-106">This tutorial shows you how to create a Windows Storage account, a blob container, creating credentials to access the storage account, writing a backup to the blob service, and performing a simple restore.</span></span> <span data-ttu-id="9c276-107">這個教學課程分成四個課程：</span><span class="sxs-lookup"><span data-stu-id="9c276-107">This tutorial is divided into four lessons:</span></span>  
  
 [<span data-ttu-id="9c276-108">第1課：建立 Azure 儲存體物件</span><span class="sxs-lookup"><span data-stu-id="9c276-108">Lesson 1: Create Azure Storage Objects</span></span>](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 <span data-ttu-id="9c276-109">在這一課，您會建立 Azure 儲存體帳戶和 Blob 容器。</span><span class="sxs-lookup"><span data-stu-id="9c276-109">In this lesson, you create an Azure storage account and a blob container.</span></span>  
  
 [<span data-ttu-id="9c276-110">第 2 課：建立 SQL Server 認證</span><span class="sxs-lookup"><span data-stu-id="9c276-110">Lesson 2: Create a SQL Server Credential</span></span>](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 <span data-ttu-id="9c276-111">在這一課，您會建立認證以儲存用來存取 Azure 儲存體帳戶的安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="9c276-111">In this lesson, you create a Credential to store security information used to access the Azure storage account.</span></span>  
  
 [<span data-ttu-id="9c276-112">第 3 課：將完整資料庫備份寫入 Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="9c276-112">Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service</span></span>](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 <span data-ttu-id="9c276-113">在這一課，您會發出 T-SQL 陳述式，以便將 AdventureWorks2012 資料庫的備份寫入 Azure Blob 儲存體服務。</span><span class="sxs-lookup"><span data-stu-id="9c276-113">In this lesson, you issue a T-SQL statement to write a backup of the AdventureWorks2012 database to the Azure Blob storage service.</span></span>  
  
 [<span data-ttu-id="9c276-114">第 4 課：從完整資料庫備份執行還原</span><span class="sxs-lookup"><span data-stu-id="9c276-114">Lesson 4: Perform a Restore From a Full Database Backup</span></span>](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 <span data-ttu-id="9c276-115">在這一課，您會發出 T-SQL 陳述式，以便從上一課建立的資料庫備份還原。</span><span class="sxs-lookup"><span data-stu-id="9c276-115">In this lesson, you issue a T-SQL statement to restore from the database backup you created in the previous lesson.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="9c276-116">需求</span><span class="sxs-lookup"><span data-stu-id="9c276-116">Requirements</span></span>  
 <span data-ttu-id="9c276-117">若要完成本教學課程，您必須熟悉 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 備份與還原概念以及 T-SQL 語法。</span><span class="sxs-lookup"><span data-stu-id="9c276-117">To complete this tutorial, you must be familiar with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore concepts and T-SQL syntax.</span></span> <span data-ttu-id="9c276-118">若要使用此教學課程，您的系統必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="9c276-118">To use this tutorial, your system must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="9c276-119">已安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的執行個體以及 AdventureWorks2012 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9c276-119">An instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], and AdventureWorks2012 database installed.</span></span>  
  
     <span data-ttu-id="9c276-120">SQL Server 執行個體可以採用內部部署，也可以位於 Azure 虛擬機器中。</span><span class="sxs-lookup"><span data-stu-id="9c276-120">The SQL Server instance can be on-premises or in an Azure Virtual Machine.</span></span>  
  
     <span data-ttu-id="9c276-121">您可以使用使用者資料庫來取代 AdventureWorks2012，並且據以修改 tsql 語法。</span><span class="sxs-lookup"><span data-stu-id="9c276-121">You can use a user database in place of AdventureWorks2012, and modify the tsql syntax accordingly.</span></span>  
  
-   <span data-ttu-id="9c276-122">用來發出 BACKUP 或 RESTORE 命令的使用者帳戶應該位於擁有 **改變任何認證** 權限的 **db_backup 運算子** 資料庫角色中。</span><span class="sxs-lookup"><span data-stu-id="9c276-122">The user account that is used to issue BACKUP or RESTORE commands should be in the **db_backup operator** database role with **Alter any credential** permissions.</span></span>  
  
### <a name="additional-reading"></a><span data-ttu-id="9c276-123">其他閱讀資料</span><span class="sxs-lookup"><span data-stu-id="9c276-123">Additional Reading</span></span>  
 <span data-ttu-id="9c276-124">以下是一些建議閱讀的主題，這些主題可讓您了解針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 備份使用 Azure Blob 儲存體服務的概念與最佳做法。</span><span class="sxs-lookup"><span data-stu-id="9c276-124">Following are some recommended reading to understand the concepts, best practices when using Azure Blob storage service for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backups.</span></span>  
  
1.  [<span data-ttu-id="9c276-125">使用 Azure Blob 儲存體服務的 SQL Server 備份及還原</span><span class="sxs-lookup"><span data-stu-id="9c276-125">SQL Server Backup and Restore with Azure Blob Storage Service</span></span>](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [<span data-ttu-id="9c276-126">SQL Server 備份至 URL 的最佳做法和疑難排解</span><span class="sxs-lookup"><span data-stu-id="9c276-126">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
