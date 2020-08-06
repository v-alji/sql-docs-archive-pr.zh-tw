---
title: 教學課程： Azure 儲存體服務中 SQL Server 資料檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 21a0fc11706a0c5ee35cf71e1af69f2927adc9db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606707"
---
# <a name="tutorial-sql-server-data-files-in-azure-storage-service"></a><span data-ttu-id="71dc8-102">教學課程：Azure 儲存體服務中的 SQL Server 資料檔案</span><span class="sxs-lookup"><span data-stu-id="71dc8-102">Tutorial: SQL Server Data Files in Azure Storage service</span></span>
  <span data-ttu-id="71dc8-103">歡迎使用 Azure 儲存體服務中的 SQL Server 資料檔案教學課程。</span><span class="sxs-lookup"><span data-stu-id="71dc8-103">Welcome to the  SQL Server Data Files in Azure Storage Service tutorial.</span></span> <span data-ttu-id="71dc8-104">本教學課程可協助您了解如何直接將 SQL Server 資料檔案儲存在 Azure Blob 儲存體服務中。</span><span class="sxs-lookup"><span data-stu-id="71dc8-104">This tutorial helps you understand how to store SQL Server data files in the Azure Blob storage service directly.</span></span>  
  
 <span data-ttu-id="71dc8-105">Azure Blob 儲存體服務的 SQL Server 整合支援是 SQL Server 2014 增強功能。</span><span class="sxs-lookup"><span data-stu-id="71dc8-105">SQL Server integration support for the Azure Blob storage service is a SQL Server 2014 enhancement.</span></span> <span data-ttu-id="71dc8-106">如需使用這項功能的功能和優點的總覽，請參閱[在 Azure 中 SQL Server 資料檔案](databases/sql-server-data-files-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="71dc8-106">For an overview of the functionality and benefits of using this functionality, see [SQL Server Data Files in Azure](databases/sql-server-data-files-in-microsoft-azure.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="71dc8-107">學習內容</span><span class="sxs-lookup"><span data-stu-id="71dc8-107">What you will learn</span></span>  
 <span data-ttu-id="71dc8-108">本教學課程示範如何在多個課程中，將 SQL Server 資料檔案儲存在 Azure 儲存體服務中。</span><span class="sxs-lookup"><span data-stu-id="71dc8-108">This tutorial shows you how to store SQL Server Data Files in Azure Storage service in multiple lessons.</span></span> <span data-ttu-id="71dc8-109">每一課都會將重點放在特定工作上。</span><span class="sxs-lookup"><span data-stu-id="71dc8-109">Each lesson is focused on a specific task.</span></span> <span data-ttu-id="71dc8-110">首先，您將瞭解如何在 Azure 中建立儲存體帳戶和容器。</span><span class="sxs-lookup"><span data-stu-id="71dc8-110">First, you will learn how to create a storage account and a container in Azure.</span></span> <span data-ttu-id="71dc8-111">然後，您將瞭解如何建立 SQL Server 認證，以便整合 SQL Server 與 Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="71dc8-111">Then, you will learn how to create a SQL Server credential to be able to integrate SQL Server with Azure Storage.</span></span> <span data-ttu-id="71dc8-112">然後，您將直接在 Azure 儲存體中建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="71dc8-112">Then, you will create a database in Azure Storage directly.</span></span> <span data-ttu-id="71dc8-113">此外，本教學課程會示範加密、移轉以及備份與還原案例。</span><span class="sxs-lookup"><span data-stu-id="71dc8-113">In addition, the tutorial will demonstrate encryption, migration, and backup and restore scenarios.</span></span>  
  
 <span data-ttu-id="71dc8-114">本教學課程分成九個課程：</span><span class="sxs-lookup"><span data-stu-id="71dc8-114">This tutorial is divided into nine lessons:</span></span>  
  
 <span data-ttu-id="71dc8-115">**[第 1 課：建立 Azure 儲存體帳戶和容器](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-115">**[Lesson 1: Create Azure Storage Account and Container](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**</span></span>  
 <span data-ttu-id="71dc8-116">在這一課，您會建立 Azure 儲存體帳戶和容器。</span><span class="sxs-lookup"><span data-stu-id="71dc8-116">In this lesson, you create an Azure Storage account and a container.</span></span>  
  
 <span data-ttu-id="71dc8-117">**[第2課。在容器上建立原則並產生共用存取簽章 &#40;SAS&#41; 金鑰](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-117">**[Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**</span></span>  
 <span data-ttu-id="71dc8-118">在這一課，您會在 Blob 容器上建立原則以及產生共用存取簽章。</span><span class="sxs-lookup"><span data-stu-id="71dc8-118">In this lesson, you create a policy on the Blob container and also generate a shared access signature.</span></span>  
  
 <span data-ttu-id="71dc8-119">**[第 3 課：建立 SQL Server 認證](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-119">**[Lesson 3: Create a SQL Server Credential](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**</span></span>  
 <span data-ttu-id="71dc8-120">在這一課，您會建立認證以儲存用來存取 Azure 儲存體帳戶的安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="71dc8-120">In this lesson, you create a Credential to store security information used to access the Azure storage account.</span></span>  
  
 <span data-ttu-id="71dc8-121">**[第 4 課：在 Azure 儲存體中建立資料庫](../relational-databases/lesson-3-database-backup-to-url.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-121">**[Lesson 4: Create a database in Azure Storage](../relational-databases/lesson-3-database-backup-to-url.md)**</span></span>  
 <span data-ttu-id="71dc8-122">在這一課，您會使用 [建立資料庫檔案名] 選項，在 Azure 儲存體中建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="71dc8-122">In this lesson, you create a database in Azure Storage using CREATE Database FILENAME option.</span></span>  
  
 <span data-ttu-id="71dc8-123">**[第5課：&#40;選擇性&#41; 使用 TDE 加密您的資料庫](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-123">**[Lesson 5. &#40;Optional&#41; Encrypt your database using TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**</span></span>  
 <span data-ttu-id="71dc8-124">在這一課，您會使用透明資料加密 (TDE) 和伺服器憑證來加密資料庫。</span><span class="sxs-lookup"><span data-stu-id="71dc8-124">In this lesson, you encrypt your database by using a transparent data encryption (TDE) and a server certificate.</span></span>  
  
 <span data-ttu-id="71dc8-125">**[第 6 課：在 Azure 中將資料庫從內部部署來源電腦移轉至目的地電腦](lesson-5-backup-database-using-file-snapshot-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-125">**[Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**</span></span>  
 <span data-ttu-id="71dc8-126">在這一課，您會使用 CREATE DATABASE FOR ATTACH 選項，將資料庫從內部部署遷移至 Azure 中的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="71dc8-126">In this lesson, you migrate a database from on-premises to a virtual machine in Azure using CREATE DATABASE FOR ATTACH option.</span></span>  
  
 <span data-ttu-id="71dc8-127">**[第 7 課：將資料檔案移至 Azure 儲存體](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-127">**[Lesson 7: Move your data files to Azure Storage](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**</span></span>  
 <span data-ttu-id="71dc8-128">在這一課，您會使用 ALTER DATABASE 語句，將資料檔案移至 Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="71dc8-128">In this lesson, you move your data files to Azure Storage using ALTER DATABASE statement.</span></span>  
  
 <span data-ttu-id="71dc8-129">**[第8課：將資料庫還原至 Azure 儲存體](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-129">**[Lesson 8. Restore a database to Azure Storage](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**</span></span>  
 <span data-ttu-id="71dc8-130">在這一課，您會使用 [還原資料庫] 移動選項，將資料庫還原到 Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="71dc8-130">In this lesson, you restore a database to Azure Storage using RESTORE Database MOVE option.</span></span>  
  
 <span data-ttu-id="71dc8-131">**[第9課：從 Azure 儲存體還原資料庫](lesson-8-restore-as-new-database-from-log-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="71dc8-131">**[Lesson 9. Restore a database from Azure Storage](lesson-8-restore-as-new-database-from-log-backup.md)**</span></span>  
 <span data-ttu-id="71dc8-132">在這一課，您會使用 [還原資料庫] [移動] 選項，從 Azure 儲存體還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="71dc8-132">In this lesson, you restore a database from Azure Storage using RESTORE Database MOVE option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71dc8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71dc8-133">See Also</span></span>  
 [<span data-ttu-id="71dc8-134">在 Azure 中 SQL Server 資料檔案</span><span class="sxs-lookup"><span data-stu-id="71dc8-134">SQL Server Data Files in Azure</span></span>](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
