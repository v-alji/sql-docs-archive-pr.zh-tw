---
title: 第4課：在 Azure 儲存體中建立資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50fca85111d5897b738e577e7735049e0b055a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606287"
---
# <a name="lesson-4-create-a-database-in-azure-storage"></a><span data-ttu-id="2a4dc-102">第 4 課：在 Azure 儲存體中建立資料庫</span><span class="sxs-lookup"><span data-stu-id="2a4dc-102">Lesson 4: Create a database in Azure Storage</span></span>
  <span data-ttu-id="2a4dc-103">在這一課，您將瞭解如何使用 Azure 中的 SQL Server 資料檔案功能來建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-103">In this lesson, you will learn how to create a database using the SQL Server Data Files in Azure feature.</span></span> <span data-ttu-id="2a4dc-104">請注意，開始進行這一課之前，您必須先完成第 1、2 和 3 課。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-104">Note that before this lesson, you must complete the Lesson 1, 2, and 3.</span></span> <span data-ttu-id="2a4dc-105">第3課是非常重要的步驟，因為您必須先將 Azure 儲存體容器及其相關聯的原則名稱和 SAS 金鑰等資訊儲存在第4課的 SQL Server 認證存放區中。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-105">Lesson 3 is a very important step because you need to store the information about your Azure storage container and its associated policy name and SAS key in the SQL Server credential store before Lesson 4.</span></span>  
  
 <span data-ttu-id="2a4dc-106">對於資料或記錄檔所使用的每一個儲存體容器，您必須建立名稱符合容器路徑的 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-106">For each storage container used by a data or log file, you must create a SQL Server Credential whose name matches the container path.</span></span> <span data-ttu-id="2a4dc-107">然後，您可以在 Azure 儲存體中建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-107">Then, you can create a new database in Azure Storage</span></span>  
  
 <span data-ttu-id="2a4dc-108">這個課程假設您已完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2a4dc-108">This lesson assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="2a4dc-109">您有 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-109">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="2a4dc-110">您已在 Azure 儲存體帳戶底下建立容器。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-110">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="2a4dc-111">您已在容器上建立具有讀取、寫入和列出權限的原則。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-111">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="2a4dc-112">您也已經產生 SAS 金鑰。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-112">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="2a4dc-113">您已在來源電腦上建立 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-113">You have created a SQL Server credential on the source machine.</span></span>  
  
 <span data-ttu-id="2a4dc-114">若要使用 Azure 儲存體功能中的 SQL Server 資料檔案在 Azure 中建立資料庫，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2a4dc-114">To create a database in Azure using the SQL Server Data Files in Azure Storage feature, follow these steps:</span></span>  
  
1.  <span data-ttu-id="2a4dc-115">連接到 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-115">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="2a4dc-116">在 [物件總管] 中連接到已安裝的 Database Engine 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-116">In Object Explorer, connect to the instance of Database Engine installed.</span></span>  
  
3.  <span data-ttu-id="2a4dc-117">在 [標準] 工具列上，按一下 [新增查詢]。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-117">On the Standard tool bar, click New Query.</span></span>  
  
4.  <span data-ttu-id="2a4dc-118">將下列範例複製並貼入查詢視窗中，並視需要修改。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-118">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="2a4dc-119">請注意，FILENAME 欄位會參考儲存體容器中資料庫檔案的 URI 路徑，該路徑的開頭必須為 https。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-119">Note that the FILENAME field refers to the URI path of the database file in storage container and it must start with https.</span></span>  
  
    ```  
  
    --Create a database that uses a SQL Server credential    
    CREATE DATABASE TestDB1    
    ON   
    (NAME = TestDB1_data,   
       FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf')   
     LOG ON   
    (NAME = TestDB1_log,   
        FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
    GO  
  
    ```  
  
     <span data-ttu-id="2a4dc-120">將一些資料加入您的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-120">Add some data to your database.</span></span>  
  
    ```  
  
    USE TestDB1;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
5.  <span data-ttu-id="2a4dc-121">若要查看內部部署 SQL Server 中的新 TestDB1，請重新整理 [物件總管] 中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-121">To see the new TestDB1 in your on-premises SQL Server, refresh databases in the Object Explorer.</span></span>  
  
6.  <span data-ttu-id="2a4dc-122">同樣地，若要查看儲存體帳戶中新建立的資料庫，請透過 SQL Server Management Studio (SSMS) 連接到儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-122">Similarly, to see the newly created database in your storage account, connect to your storage account via SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="2a4dc-123">如需如何使用 SQL Server Management Studio 連接到 Azure 儲存體的相關資訊，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2a4dc-123">For information on how to connect to an Azure storage using SQL Server Management Studio, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="2a4dc-124">首先，取得儲存體帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-124">First, get the storage account information.</span></span> <span data-ttu-id="2a4dc-125">登入管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-125">Log in to the Management Portal.</span></span> <span data-ttu-id="2a4dc-126">然後，按一下 **[儲存體]** 並選擇您的儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-126">Then, click **Storage** and choose your storage account.</span></span> <span data-ttu-id="2a4dc-127">選取儲存體帳戶後，按一下頁面底部的 **[管理存取金鑰]** 。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-127">When a storage account is selected, click **Manage Access Keys** at the bottom of the page.</span></span> <span data-ttu-id="2a4dc-128">這樣會開啟類似的對話方塊視窗：</span><span class="sxs-lookup"><span data-stu-id="2a4dc-128">This opens a similar dialog window:</span></span>  
  
         <span data-ttu-id="2a4dc-129">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="2a4dc-129">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")</span></span>  
  
    2.  <span data-ttu-id="2a4dc-130">將 [**儲存體帳戶名稱**] 和 [**主要存取金鑰**] 值複製到 SSMS 中的 [**連接到 Azure 儲存體**] 對話方塊視窗。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-130">Copy the **Storage Account Name** and **Primary Access Key** values to the **Connect to Azure Storage** dialog window in SSMS.</span></span> <span data-ttu-id="2a4dc-131">然後按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-131">Then, click **Connect**.</span></span> <span data-ttu-id="2a4dc-132">這樣就會將有關儲存體帳戶容器的資訊帶到 SSMS 中，如下列螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="2a4dc-132">This brings the information about storage account containers to SSMS as shown in the following screenshot:</span></span>  
  
         <span data-ttu-id="2a4dc-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="2a4dc-133">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="2a4dc-134">下列螢幕擷取畫面示範內部部署和 Azure 儲存體環境中新建立的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-134">The following screenshot demonstrates the new created database both in on-premises and Azure Storage environment.</span></span>  
  
 <span data-ttu-id="2a4dc-135">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="2a4dc-135">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="2a4dc-136">**注意：** 如果容器中有任何作用中的資料檔案參考，則任何嘗試刪除相關聯 SQL Server 認證的動作都會失敗。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-136">**Note:** If there are any active references to data files in a container, any attempts to delete the associated SQL Server credential fails.</span></span> <span data-ttu-id="2a4dc-137">同樣地，如果 Blob 中特定資料庫檔案上已有租用，而您想要將它刪除，則必須先中斷 Blob 上的租用。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-137">Similarly, if there is already a lease on a specific database file in a blob and you want to delete it, first you need to break the lease on the blob.</span></span> <span data-ttu-id="2a4dc-138">若要中斷租用，您可以使用 [租用 Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-138">To break the lease, you can use [Lease Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx).</span></span>  
  
 <span data-ttu-id="2a4dc-139">使用這項新功能就可以設定 SQL Server，讓所有 CREATE DATABASE 陳述式都預設為具備雲端能力的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-139">Using this new feature, you can configure SQL Server so that any CREATE DATABASE statement will default to a cloud enabled database.</span></span> <span data-ttu-id="2a4dc-140">換句話說，您可以在 SQL Server Management Studio 伺服器實例屬性中設定預設資料和記錄檔位置，如此一來，每當您建立資料庫時，就會在 Azure 儲存體中將所有資料庫檔案 ( .mdf、.ldf) 建立為分頁 blob。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-140">In other words, you can set default data and log locations in SQL Server Management Studio Server instance properties so anytime you create a database, all database files (.mdf, .ldf) are created as page blobs in Azure Storage.</span></span>  
  
 <span data-ttu-id="2a4dc-141">若要使用 SQL Server Management Studio 使用者介面在 Azure 儲存體中建立資料庫，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2a4dc-141">To create a database in Azure Storage by using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="2a4dc-142">在 [物件總管] 中，連接到 SQL Server Database Engine 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-142">In Object Explorer, connect to an instance of the SQL Server Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="2a4dc-143">以滑鼠右鍵按一下 [資料庫]，然後按一下 [新增資料庫]。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-143">Right-click Databases, and then click New Database.</span></span>  
  
3.  <span data-ttu-id="2a4dc-144">在 [新增資料庫] 對話方塊視窗中，輸入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-144">In the New Database dialog window, type a database name.</span></span>  
  
4.  <span data-ttu-id="2a4dc-145">變更主要資料與交易記錄檔的預設值，然後在 [資料庫檔案] 方格中按一下適當的資料格，並輸入新的值。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-145">Change the default values of the primary data and transaction log files, in the Database files grid, click the appropriate cell and enter the new value.</span></span> <span data-ttu-id="2a4dc-146">另外，指定檔案位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-146">Also, specify the path for the file location.</span></span> <span data-ttu-id="2a4dc-147">針對 Path 輸入儲存體容器的 URL 路徑，例如 `https://teststorageaccnt.blob.core.windows.net/testcontainer/`。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-147">For Path, type the URL path of the storage container, such as `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.</span></span> <span data-ttu-id="2a4dc-148">針對 FileName 輸入資料庫檔案 (.mdf、.ldf) 的實體檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-148">For FileName, type the physical file names of the database files (.mdf, .ldf).</span></span>  
  
     <span data-ttu-id="2a4dc-149">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="2a4dc-149">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")</span></span>  
  
     <span data-ttu-id="2a4dc-150">如需詳細資訊，請參閱 [將資料或記錄檔加入資料庫](databases/add-data-or-log-files-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-150">For more information, see [Add Data or Log Files to a Database](databases/add-data-or-log-files-to-a-database.md).</span></span>  
  
5.  <span data-ttu-id="2a4dc-151">保留所有其他預設值。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-151">Keep all other default values.</span></span>  
  
6.  <span data-ttu-id="2a4dc-152">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-152">Click OK.</span></span>  
  
 <span data-ttu-id="2a4dc-153">若要查看內部部署 SQL Server 中的新 TestDB1，請重新整理 [物件總管] 中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-153">To see the new TestDB1 in your on-premises SQL Server, refresh databases in the Object Explorer.</span></span> <span data-ttu-id="2a4dc-154">同樣地，若要查看儲存體帳戶中新建立的資料庫，請依照本課程先前的說明，透過 SQL Server Management Studio (SSMS) 連接到儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a4dc-154">Similarly, to see the newly created database in your storage account, connect to your storage account via SQL Server Management Studio (SSMS) as explained earlier in this lesson.</span></span>  
  
 <span data-ttu-id="2a4dc-155">**下一課：**</span><span class="sxs-lookup"><span data-stu-id="2a4dc-155">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="2a4dc-156">第5課：&#40;選擇性&#41; 使用 TDE 加密您的資料庫</span><span class="sxs-lookup"><span data-stu-id="2a4dc-156">Lesson 5. &#40;Optional&#41; Encrypt your database using TDE</span></span>](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  
