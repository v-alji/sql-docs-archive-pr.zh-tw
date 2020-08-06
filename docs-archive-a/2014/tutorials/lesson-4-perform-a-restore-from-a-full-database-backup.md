---
title: 第4課：從完整資料庫備份執行還原 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9906ea14c2f76a49644a8f76fbd894adf8b9d500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594873"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a><span data-ttu-id="34e6a-102">第 4 課：從完整資料庫備份執行還原</span><span class="sxs-lookup"><span data-stu-id="34e6a-102">Lesson 4: Perform a Restore From a Full Database Backup</span></span>
  <span data-ttu-id="34e6a-103">這一課將示範如何使用 tsql 陳述式，從上一課建立的完整資料庫備份執行還原。</span><span class="sxs-lookup"><span data-stu-id="34e6a-103">This lesson demonstrates the use of a tsql statement to perform a restore from a full database backup created in the previous lesson.</span></span>  
  
## <a name="perform-a-restore-of-a-database-backup"></a><span data-ttu-id="34e6a-104">執行資料庫備份的還原</span><span class="sxs-lookup"><span data-stu-id="34e6a-104">Perform a Restore of a Database Backup</span></span>  
 <span data-ttu-id="34e6a-105">若要還原完整資料庫備份，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="34e6a-105">To restore a full database backup, use the following steps:</span></span>  
  
1.  <span data-ttu-id="34e6a-106">連接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="34e6a-106">Connect to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="34e6a-107">在 **[物件總管]** 中，連接到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="34e6a-107">In the **Object Explorer**, connect to the instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
3.  <span data-ttu-id="34e6a-108">在 [標準] 功能表列上，按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="34e6a-108">On the Standard menu bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="34e6a-109">將下列範例複製並貼入查詢視窗中，並視需要修改。</span><span class="sxs-lookup"><span data-stu-id="34e6a-109">Copy and paste the following example into the query window, modify as needed.</span></span>  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  <span data-ttu-id="34e6a-110">確認 T-sql 語句，然後按一下 [**執行**]</span><span class="sxs-lookup"><span data-stu-id="34e6a-110">Verify the T-SQL statement and click **Execute**</span></span>  
  
### <a name="return-to-tutorials-portal"></a><span data-ttu-id="34e6a-111">返回教學課程入口網站</span><span class="sxs-lookup"><span data-stu-id="34e6a-111">Return to Tutorials Portal</span></span>  
 <span data-ttu-id="34e6a-112">[教學課程： SQL Server 備份和還原至 Azure Blob 儲存體服務](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="34e6a-112">[Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).</span></span>  
  
  
