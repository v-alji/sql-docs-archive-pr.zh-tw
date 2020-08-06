---
title: 第7課：將資料檔案移至 Azure 儲存體 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 753863d7b8b8d8fa554f1579bee6837c525efd9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598370"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a><span data-ttu-id="f9091-102">第 7 課：將資料檔案移至 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="f9091-102">Lesson 7: Move your data files to Azure Storage</span></span>
  <span data-ttu-id="f9091-103">在這一課，您將瞭解如何將資料檔案移至 Azure 儲存體 (，但不會) SQL Server 實例。</span><span class="sxs-lookup"><span data-stu-id="f9091-103">In this lesson, you will learn how to move your data files to Azure Storage (but not your SQL Server instance).</span></span> <span data-ttu-id="f9091-104">進行這一課並不需要完成第 4、5 和 6 課。</span><span class="sxs-lookup"><span data-stu-id="f9091-104">To follow this lesson, you do not need to complete Lesson 4, 5, and 6.</span></span>  
  
 <span data-ttu-id="f9091-105">若要將資料檔案移至 Azure 儲存體，您可以使用 `ALTER DATABASE` 語句，因為它可協助您變更資料檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="f9091-105">To move your data files to Azure Storage, you can use the `ALTER DATABASE` statement as it helps to change the location of the data files.</span></span>  
  
 <span data-ttu-id="f9091-106">這個課程假設您已完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f9091-106">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="f9091-107">您有 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="f9091-107">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="f9091-108">您已在 Azure 儲存體帳戶底下建立容器。</span><span class="sxs-lookup"><span data-stu-id="f9091-108">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="f9091-109">您已在容器上建立具有讀取、寫入和列出權限的原則。</span><span class="sxs-lookup"><span data-stu-id="f9091-109">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="f9091-110">您也已經產生 SAS 金鑰。</span><span class="sxs-lookup"><span data-stu-id="f9091-110">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="f9091-111">您已在來源電腦上建立 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="f9091-111">You have created a SQL Server credential on the source machine.</span></span>  
  
 <span data-ttu-id="f9091-112">接下來，使用下列步驟將您的資料檔案移至 Azure 儲存體：</span><span class="sxs-lookup"><span data-stu-id="f9091-112">Next, use the following steps to move your data files to Azure Storage:</span></span>  
  
1.  <span data-ttu-id="f9091-113">首先，在來源電腦中建立測試資料庫，並在其中加入一些資料。</span><span class="sxs-lookup"><span data-stu-id="f9091-113">First, create a test database in the source machine and add some data to it.</span></span>  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  <span data-ttu-id="f9091-114">執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="f9091-114">Run the following code:</span></span>  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  <span data-ttu-id="f9091-115">當您執行此動作時，您會看到下列訊息：「系統目錄中的檔案 "TestDB1Alter" 已修改。</span><span class="sxs-lookup"><span data-stu-id="f9091-115">When you run this, you will see this message: "The file "TestDB1Alter" has been modified in the system catalog.</span></span> <span data-ttu-id="f9091-116">新的路徑將會在下一次資料庫啟動時使用。」</span><span class="sxs-lookup"><span data-stu-id="f9091-116">The new path will be used the next time the database is started."</span></span>  
  
4.  <span data-ttu-id="f9091-117">然後將資料庫設為離線。</span><span class="sxs-lookup"><span data-stu-id="f9091-117">Then, set the database offline.</span></span>  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  <span data-ttu-id="f9091-118">現在，您必須使用下列其中一種方法，將資料檔案複製到 Azure 儲存體： [AzCopy 工具](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs)、 [Put 頁面](https://msdn.microsoft.com/library/azure/ee691975.aspx)、[儲存體用戶端程式庫參考](https://msdn.microsoft.com/library/azure/dn261237.aspx)，或協力廠商儲存體瀏覽器工具。</span><span class="sxs-lookup"><span data-stu-id="f9091-118">Now, you need to copy the data files to Azure Storage by using one of the following methods: [AzCopy Tool](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx), or a third-party storage explorer tool.</span></span>  
  
     <span data-ttu-id="f9091-119">**重要事項：** 使用這項新的增強功能時，請務必確定您建立的是分頁 Blob，而不是區塊 Blob。</span><span class="sxs-lookup"><span data-stu-id="f9091-119">**Important:** When using this new enhancement, always make sure that you create a page blob not a block blob.</span></span>  
  
6.  <span data-ttu-id="f9091-120">然後將資料庫設為線上。</span><span class="sxs-lookup"><span data-stu-id="f9091-120">Then, set the database online.</span></span>  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 <span data-ttu-id="f9091-121">**下一課：**</span><span class="sxs-lookup"><span data-stu-id="f9091-121">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="f9091-122">第8課：將資料庫還原至 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="f9091-122">Lesson 8. Restore a database to Azure Storage</span></span>](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
