---
title: 第3課：將完整資料庫備份寫入 Azure Blob 儲存體服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 17e7e6b608d248a48cde52f1107bb910f06d64ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686566"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-azure-blob-storage-service"></a><span data-ttu-id="3954f-102">第 3 課：將完整資料庫備份寫入 Azure Blob 儲存體服務</span><span class="sxs-lookup"><span data-stu-id="3954f-102">Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service</span></span>
  <span data-ttu-id="3954f-103">這一課將示範如何使用 tsql 語句來執行 Azure Blob 儲存體服務的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="3954f-103">This lesson demonstrates the use of tsql statement to perform a full database backup to Azure Blob storage service.</span></span>  
  
## <a name="perform-a-full-database-backup-to-the-azure-blob-storage-service"></a><span data-ttu-id="3954f-104">執行 Azure Blob 儲存體服務的完整資料庫備份</span><span class="sxs-lookup"><span data-stu-id="3954f-104">Perform a Full Database Backup to the Azure Blob Storage Service</span></span>  
 <span data-ttu-id="3954f-105">若要建立完整資料庫備份，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3954f-105">To create a full database backup, use the following steps:</span></span>  
  
1.  <span data-ttu-id="3954f-106">連接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3954f-106">Connect to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="3954f-107">在 **[物件總管]** 中，連接到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3954f-107">In the **Object Explorer**, connect to the instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
3.  <span data-ttu-id="3954f-108">在 [標準] 功能表列上，按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="3954f-108">On the Standard menu bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="3954f-109">將下列範例複製並貼入查詢視窗中、視需要修改，然後按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="3954f-109">Copy and paste the following example into the query window, modify as needed, and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  <span data-ttu-id="3954f-110">在 [物件總管] 中，連接到 Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="3954f-110">In the object explorer, connect to Azure Storage.</span></span> <span data-ttu-id="3954f-111">瀏覽並尋找容器以及新建立的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="3954f-111">Browse to find the container and the newly created backup files.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="3954f-112">下一課</span><span class="sxs-lookup"><span data-stu-id="3954f-112">Next Lesson</span></span>  
 <span data-ttu-id="3954f-113">[第4課：從完整資料庫備份執行還原](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)。</span><span class="sxs-lookup"><span data-stu-id="3954f-113">[Lesson 4: Perform a Restore From a Full Database Backup](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).</span></span>  
  
  
