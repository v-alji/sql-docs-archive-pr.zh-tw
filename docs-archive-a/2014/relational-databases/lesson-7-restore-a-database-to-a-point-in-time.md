---
title: 第 8 課： 將資料庫還原至 Azure 儲存體 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: adec725d1b519fb67560dc572823ba0a116aaa54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606284"
---
# <a name="lesson-8-restore-a-database-to-azure-storage"></a><span data-ttu-id="57ea7-103">第 8 課：</span><span class="sxs-lookup"><span data-stu-id="57ea7-103">Lesson 8.</span></span> <span data-ttu-id="57ea7-104">將資料庫還原到 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="57ea7-104">Restore a database to Azure Storage</span></span>
  <span data-ttu-id="57ea7-105">在這一課，您將學習如何在本機建立備份檔案，然後將它還原到 Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="57ea7-105">In this lesson, you will learn how to create a backup file locally and then restore it to Azure Storage.</span></span> <span data-ttu-id="57ea7-106">請注意，您可以將資料庫置於內部部署或 Azure 虛擬機器中。</span><span class="sxs-lookup"><span data-stu-id="57ea7-106">Note that you can have your database either on either on-premises or in a virtual machine in Azure.</span></span> <span data-ttu-id="57ea7-107">進行這一課並不需要完成第 4、5、6 和 7 課。</span><span class="sxs-lookup"><span data-stu-id="57ea7-107">To follow this lesson, you do not need to complete Lesson 4, 5, 6, and 7.</span></span>  
  
 <span data-ttu-id="57ea7-108">這個課程假設您已完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="57ea7-108">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="57ea7-109">您有 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="57ea7-109">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="57ea7-110">您已在 Azure 儲存體帳戶底下建立容器。</span><span class="sxs-lookup"><span data-stu-id="57ea7-110">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="57ea7-111">您已在容器上建立具有讀取、寫入和列出權限的原則。</span><span class="sxs-lookup"><span data-stu-id="57ea7-111">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="57ea7-112">您也已經產生 SAS 金鑰。</span><span class="sxs-lookup"><span data-stu-id="57ea7-112">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="57ea7-113">您已在來源電腦上根據共用存取簽章建立 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="57ea7-113">You have created a SQL Server credential on the source machine based on Shared Access Signature.</span></span>  
  
-   <span data-ttu-id="57ea7-114">您已在來源電腦上建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="57ea7-114">You have created a database in the source machine.</span></span>  
  
 <span data-ttu-id="57ea7-115">若要將資料庫還原成 Azure 儲存體，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="57ea7-115">To restore a database to Azure Storage, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="57ea7-116">在來源電腦中啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="57ea7-116">In the source machine, start SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="57ea7-117">連接到新建立的資料庫時，開啟查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="57ea7-117">When connected to the newly created database, open the query window.</span></span> <span data-ttu-id="57ea7-118">執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="57ea7-118">Run the following statement:</span></span>  
  
    ```sql  
  
    USE TestDB3Restore;   
    GO   
    BACKUP DATABASE TestDB3Restore   
    TO DISK = 'C:\BACKUP\TestDB3Restore.Bak'   
       WITH FORMAT,   
       NAME = 'Full Backup of TestDB3Restore'   
    GO  
  
    ```  
  
3.  <span data-ttu-id="57ea7-119">接著，在 [查詢] 視窗中複製並執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="57ea7-119">Next, copy and run the following statements in the Query window.</span></span>  
  
    ```sql  
  
    USE master;   
    GO   
    RESTORE DATABASE TestDB3Restore    
    FROM DISK = 'C:\BACKUP\TestDB3Restore.bak'    
    WITH REPLACE,   
    MOVE 'TestDB3Restore' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore.mdf',     
    MOVE 'TestDB3Restore_log' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore_log.ldf';   
    GO  
  
    ```  
  
     <span data-ttu-id="57ea7-120">在這個步驟最後，您的容器應該會列出管理入口網站上的資料檔案 (.mdf) 和 (.ldf)。</span><span class="sxs-lookup"><span data-stu-id="57ea7-120">At the end of this step, your container should list data (.mdf) and (.ldf) files on the Management Portal.</span></span>  
  
 <span data-ttu-id="57ea7-121">若要使用 SQL Server Management Studio 使用者介面來還原具有指向 Azure 儲存體之資料和記錄檔的資料庫，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="57ea7-121">To restore a database with data and log files pointing to Azure Storage using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="57ea7-122">在**物件總管**中，按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="57ea7-122">In **Object Explorer**, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="57ea7-123">展開 [**資料庫**]，然後選取您的資料庫。</span><span class="sxs-lookup"><span data-stu-id="57ea7-123">Expand **Databases**, and, select your database.</span></span>  
  
3.  <span data-ttu-id="57ea7-124">以滑鼠右鍵按一下資料庫，指向 [工作]  ，然後按一下 [還原]  。</span><span class="sxs-lookup"><span data-stu-id="57ea7-124">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="57ea7-125">在 [**一般**] 頁面的 [**還原**來源] 區段中，按一下 [**來源**裝置]。</span><span class="sxs-lookup"><span data-stu-id="57ea7-125">On the **General** page, in the **Restore** source section, click **Source** device.</span></span>  
  
5.  <span data-ttu-id="57ea7-126">按一下 [**來源**裝置] 文字方塊的 [流覽] 按鈕，這會開啟 [**選取備份裝置**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="57ea7-126">Click the browse button for the **Source** device text box, which opens the **Select Backup Devices** dialog box.</span></span>  
  
6.  <span data-ttu-id="57ea7-127">在 [備份媒體] 文字方塊中，**選取 [** 檔案]，然後按一下 [**新增**] 按鈕，找出備份 ( .bak) 檔案。</span><span class="sxs-lookup"><span data-stu-id="57ea7-127">In the Backup media text box, select **File**, and click the **Add** button to locate the backup (.bak) file.</span></span> <span data-ttu-id="57ea7-128">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="57ea7-128">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="57ea7-129">按一下第一頁**上的 [** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="57ea7-129">Click **Files** on the first page.</span></span>  
  
8.  <span data-ttu-id="57ea7-130">在 [將**資料庫檔案還原**為] 區段的 [**還原為**] 欄位底下，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="57ea7-130">In the **Restore Database Files** as section, under **Restore As** field, type the followings:</span></span>  
  
     <span data-ttu-id="57ea7-131">針對 [資料檔案]，輸入： `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf` 。</span><span class="sxs-lookup"><span data-stu-id="57ea7-131">For data file, type: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`.</span></span> <span data-ttu-id="57ea7-132">在 [記錄檔] 中，輸入： `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf` 。</span><span class="sxs-lookup"><span data-stu-id="57ea7-132">For log file, type: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`.</span></span>  
  
     <span data-ttu-id="57ea7-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="57ea7-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")</span></span>  
  
9. <span data-ttu-id="57ea7-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="57ea7-134">Click **OK**.</span></span>  
  
 <span data-ttu-id="57ea7-135">還原完成時，登入管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="57ea7-135">When the restore is done, log in to the Management Portal.</span></span> <span data-ttu-id="57ea7-136">您應該能夠在容器中看見 .mdf 和 .ldf 檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="57ea7-136">You should be able to see the .mdf and .ldf files in the container as follows:</span></span>  
  
 <span data-ttu-id="57ea7-137">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="57ea7-137">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="57ea7-138">**下一課：**</span><span class="sxs-lookup"><span data-stu-id="57ea7-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="57ea7-139">第9課：從 Azure 儲存體還原資料庫</span><span class="sxs-lookup"><span data-stu-id="57ea7-139">Lesson 9. Restore a database from Azure Storage</span></span>](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
