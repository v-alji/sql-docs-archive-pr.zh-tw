---
title: 第6課：將資料庫從內部部署的來源機器遷移至 Azure 中的目的地機器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9af8a260493561f9728d1677b7667bd3f36cb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598371"
---
# <a name="lesson-6-migrate-a-database-from-a-source-machine-on-premises-to-a-destination-machine-in-azure"></a><span data-ttu-id="b5049-102">第 6 課：在 Azure 中將資料庫從內部部署來源電腦移轉至目的地電腦</span><span class="sxs-lookup"><span data-stu-id="b5049-102">Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure</span></span>
  <span data-ttu-id="b5049-103">本課程假設您已有另一個 SQL Server，其可能位於另一個內部部署電腦或 Azure 中的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="b5049-103">This lesson assumes that you already have another SQL Server, which might reside in another on-premises computer or in a virtual machine in Azure.</span></span> <span data-ttu-id="b5049-104">如需有關如何在 Azure 中建立 SQL Server 虛擬機器的詳細資訊，請參閱[在 azure 上布建 SQL Server 虛擬機器](https://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/)。</span><span class="sxs-lookup"><span data-stu-id="b5049-104">For information on how to create a SQL Server virtual machine in Azure, see [Provisioning a SQL Server Virtual Machine on Azure](https://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/).</span></span> <span data-ttu-id="b5049-105">在 Azure 中布建 SQL Server 虛擬機器之後，請確定您可以透過另一部電腦中的 SQL Server Management Studio，連接到這部虛擬機器中 SQL Server 的實例。</span><span class="sxs-lookup"><span data-stu-id="b5049-105">After provisioning a SQL Server virtual machine in Azure, make sure that you can connect to an instance of SQL Server in this virtual machine via SQL Server Management Studio in another computer.</span></span>  
  
 <span data-ttu-id="b5049-106">這個課程同樣假設您已完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b5049-106">This lesson also assumes that you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="b5049-107">您有 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="b5049-107">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="b5049-108">您已在 Azure 儲存體帳戶底下建立容器。</span><span class="sxs-lookup"><span data-stu-id="b5049-108">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="b5049-109">您已在容器上建立具有讀取、寫入和列出權限的原則。</span><span class="sxs-lookup"><span data-stu-id="b5049-109">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="b5049-110">您也已經產生 SAS 金鑰。</span><span class="sxs-lookup"><span data-stu-id="b5049-110">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="b5049-111">您已在來源電腦上建立 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="b5049-111">You have created a SQL Server credential on the source machine.</span></span>  
  
-   <span data-ttu-id="b5049-112">您已經在 Azure 中建立目的地 SQL Server 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="b5049-112">You already have created a destination SQL Server virtual machine in Azure.</span></span> <span data-ttu-id="b5049-113">我們建議您藉由選取包含 SQL Server 2014 的平台映像來建立它。</span><span class="sxs-lookup"><span data-stu-id="b5049-113">We recommend that you create it by selecting a platform image that includes SQL Server 2014.</span></span>  
  
 <span data-ttu-id="b5049-114">若要將資料庫從內部部署 SQL Server 遷移至 Azure 中的另一部虛擬機器，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="b5049-114">To migrate a database from SQL Server on-premises to another virtual machine in Azure, you can follow these steps:</span></span>  
  
1.  <span data-ttu-id="b5049-115">在來源電腦上 (在本教學課程中為內部部署電腦)，於 SQL Server Management Studio 中開啟查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="b5049-115">In the source machine (which is an on-premises computer in this tutorial), open a query window in SQL Server Management Studio.</span></span> <span data-ttu-id="b5049-116">卸離資料庫，藉由執行下列陳述式將它移至另一部電腦：</span><span class="sxs-lookup"><span data-stu-id="b5049-116">Detach your database to move it to another machine by executing these statements:</span></span>  
  
    ```  
    -- Detach the database in the source machine   
    USE master  
    EXEC sp_detach_db 'TestDB1', 'true';  
    ```  
  
2.  <span data-ttu-id="b5049-117">如果您需要將資料庫傳送至目的地電腦，則必須先備妥目的地電腦。</span><span class="sxs-lookup"><span data-stu-id="b5049-117">If you need to transfer a database to a destination machine, first you must prepare it.</span></span> <span data-ttu-id="b5049-118">若要準備目的地電腦，您需要先在目的地電腦上建立 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="b5049-118">To prepare your destination machine, first you need to create a SQL Server credential in the destination machine.</span></span> <span data-ttu-id="b5049-119">如果它是加密的資料庫，則同樣需要從來源電腦將憑證匯入至目的地電腦。</span><span class="sxs-lookup"><span data-stu-id="b5049-119">If it is an encrypted database, you need to import the certificate from the source machine to the destination machine as well.</span></span>  
  
    1.  <span data-ttu-id="b5049-120">若要在目的地電腦上建立 SQL Server 認證，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b5049-120">To create a SQL Server Credential in the destination machine, follow these steps:</span></span>  
  
        1.  <span data-ttu-id="b5049-121">透過來源電腦上的 SQL Server Management Studio 連接到目的地電腦。</span><span class="sxs-lookup"><span data-stu-id="b5049-121">Connect to the destination machine via SQL Server Management Studio in your source computer.</span></span>  <span data-ttu-id="b5049-122">或者，直接在目的地電腦上啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="b5049-122">Or, start SQL Server Management Studio in your destination computer directly.</span></span>  
  
        2.  <span data-ttu-id="b5049-123">在 [標準] 工具列上，按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="b5049-123">On the Standard tool bar, click **New Query**.</span></span>  
  
        3.  <span data-ttu-id="b5049-124">將下列範例複製並貼入查詢視窗中，並視需要修改。</span><span class="sxs-lookup"><span data-stu-id="b5049-124">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="b5049-125">下列語句會建立 SQL Server 認證，以儲存儲存體容器的共用存取憑證。</span><span class="sxs-lookup"><span data-stu-id="b5049-125">The following statement creates a SQL Server Credential to store your storage container's Shared Access Certificate.</span></span>  
  
            ```sql  
  
            USE master   
            GO   
            CREATE CREDENTIAL [http://teststorageaccnt.blob.core.windows.net/testcontainer]   
            WITH IDENTITY='SHARED ACCESS SIGNATURE',   
            SECRET = 'your SAS key'   
            GO  
  
            ```  
  
        4.  <span data-ttu-id="b5049-126">若要查看所有可用的認證，可以在查詢視窗中執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b5049-126">To see all available credentials, you can run the following statement in the query window:</span></span>  
  
            ```sql  
            SELECT * from sys.credentials   
            ```  
  
        5.  <span data-ttu-id="b5049-127">連接到目的地伺服器時，開啟查詢視窗，並執行：</span><span class="sxs-lookup"><span data-stu-id="b5049-127">When connected to the destination server, open query window, and run:</span></span>  
  
            ```sql  
  
            -- Create a master key and a server certificate   
            USE master   
            GO   
            CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01'; -- You may use a different password.   
            GO   
            CREATE CERTIFICATE MySQLCert   
            FROM FILE = 'C:\certs\MySQLCert.CER'   
            WITH PRIVATE KEY   
            (   
            FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
            DECRYPTION BY PASSWORD = 'MySQLKey01'   
            );   
            GO  
  
            ```  
  
             <span data-ttu-id="b5049-128">這個步驟結束時，目的地電腦已匯入備份自來源電腦的加密憑證。</span><span class="sxs-lookup"><span data-stu-id="b5049-128">At the end of this step, the destination machine has imported the encryption certificate that was backed up from the source machine.</span></span> <span data-ttu-id="b5049-129">接著，您可以在目的地電腦中附加資料檔案。</span><span class="sxs-lookup"><span data-stu-id="b5049-129">Next, you can attach the data files in the destination machine.</span></span>  
  
    2.  <span data-ttu-id="b5049-130">然後，使用 FOR ATTACH 選項，建立資料庫，其中包含指向 Azure 儲存體中現有檔案的資料和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b5049-130">Then, create a database with data and log files pointing to the existing files in Azure Storage by using FOR ATTACH option.</span></span> <span data-ttu-id="b5049-131">在查詢視窗中，執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b5049-131">In the query window, run the following statement:</span></span>  
  
        ```sql  
  
        --Create a database on the destination server   
        CREATE DATABASE TestDB1onDest   
        ON   
        (NAME = TestDB1_data,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf' )   
        LOG ON   
         (NAME = TestDB1_log,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
        FOR ATTACH   
        GO  
  
        ```  
  
    3.  <span data-ttu-id="b5049-132">在 [物件總管] 中按一下 [資料庫]，然後以滑鼠右鍵按一下 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="b5049-132">On the Object Explorer, click Databases, right-click Refresh.</span></span> <span data-ttu-id="b5049-133">您應該能夠看到列出的新建立資料庫 TestDB1onDest。</span><span class="sxs-lookup"><span data-stu-id="b5049-133">You should be able to see the newly created database TestDB1onDest listed.</span></span>  
  
    4.  <span data-ttu-id="b5049-134">接著在查詢視窗中執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b5049-134">Next, run the following statement in the query window:</span></span>  
  
        ```sql  
  
        USE TestDB1onDest   
        SELECT * FROM Table1;   
        GO  
  
        ```  
  
         <span data-ttu-id="b5049-135">這樣應該會列出您在第 4 課中輸入的所有資料。</span><span class="sxs-lookup"><span data-stu-id="b5049-135">This should list all the data you entered in Lesson 4.</span></span>  
  
 <span data-ttu-id="b5049-136">請注意，加密的資料庫已傳送到另一個計算執行個體，且未移動任何資料。</span><span class="sxs-lookup"><span data-stu-id="b5049-136">Note that the encrypted database was transferred to another compute instance with no data movement.</span></span>  
  
 <span data-ttu-id="b5049-137">若要使用 SQL Server Management Studio 使用者介面來建立具有指向 Azure 儲存體中現有檔案之資料和記錄檔的資料庫，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b5049-137">To create a database with data and log files pointing to the existing files in Azure Storage using SQL Server Management Studio user interface, perform these steps:</span></span>  
  
1.  <span data-ttu-id="b5049-138">在物件總管中，連接到 SQL Server Database Engine 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="b5049-138">In **Object Explorer**, connect to an instance of the SQL Server Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="b5049-139">以滑鼠右鍵按一下 [資料庫]，然後按一下 [新增資料庫]。</span><span class="sxs-lookup"><span data-stu-id="b5049-139">Right-click **Databases**, and then click **New Database**.</span></span> <span data-ttu-id="b5049-140">然後，以滑鼠右鍵按一下 [TestDB1]。</span><span class="sxs-lookup"><span data-stu-id="b5049-140">Then, right-click TestDB1.</span></span> <span data-ttu-id="b5049-141">按一下 [工作]，然後按一下 [卸離]。</span><span class="sxs-lookup"><span data-stu-id="b5049-141">Click Tasks, and then click Detach.</span></span> <span data-ttu-id="b5049-142">在 [卸離] 對話方塊視窗中，選取 [卸除連接]。</span><span class="sxs-lookup"><span data-stu-id="b5049-142">In the Detach dialog window, check Drop Connections.</span></span> <span data-ttu-id="b5049-143">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b5049-143">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="b5049-144">連接到具有 SQL Server 2014 CTP2 或更新版本的目的地電腦。</span><span class="sxs-lookup"><span data-stu-id="b5049-144">Connect to the destination machine, which has SQL Server 2014 CTP2 or later.</span></span> <span data-ttu-id="b5049-145">若要準備目的地電腦，您需要在目的地電腦上建立 SQL Server 認證，並指向放置 TestDB1 的相同容器。</span><span class="sxs-lookup"><span data-stu-id="b5049-145">To prepare your destination machine, you need to create a SQL Server credential in the destination machine to point to the same container that you put TestDB1 in.</span></span> <span data-ttu-id="b5049-146">如果您要在同一部電腦上重新附加，則不需要建立另一個認證。</span><span class="sxs-lookup"><span data-stu-id="b5049-146">If you are going to re-attach in the same computer, you do not need to create another credential.</span></span>  
  
4.  <span data-ttu-id="b5049-147">在**物件總管**中，以滑鼠右鍵按一下 [**資料庫**]，然後按一下 [**附加**]。</span><span class="sxs-lookup"><span data-stu-id="b5049-147">In **Object Explorer**, right-click **Databases** and click **Attach**.</span></span>  
  
5.  <span data-ttu-id="b5049-148">在 [**附加資料庫**] 對話方塊中，若要指定要附加的資料庫，請按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="b5049-148">In the **Attach Databases** dialog box, to specify the database to be attached, click **Add**.</span></span> <span data-ttu-id="b5049-149">在 [**尋找資料庫**檔案] 對話方塊視窗中：</span><span class="sxs-lookup"><span data-stu-id="b5049-149">In the **Locate Database Files** dialog window:</span></span>  
  
     <span data-ttu-id="b5049-150">針對 [資料庫資料檔案位置]，輸入： `https://teststorageaccnt.blob.core.windows.net/testcontainer/` 。</span><span class="sxs-lookup"><span data-stu-id="b5049-150">For Database Data File Location, type: `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.</span></span>  
  
     <span data-ttu-id="b5049-151">針對 [檔案名]，輸入： `TestDB1Data.mdf` 。</span><span class="sxs-lookup"><span data-stu-id="b5049-151">For File name, type: `TestDB1Data.mdf`.</span></span>  
  
6.  <span data-ttu-id="b5049-152">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b5049-152">Click **OK**.</span></span>  
  
     <span data-ttu-id="b5049-153">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="b5049-153">![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")</span></span>  
  
 <span data-ttu-id="b5049-154">**下一課：**</span><span class="sxs-lookup"><span data-stu-id="b5049-154">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="b5049-155">第 7 課：將資料檔案移至 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="b5049-155">Lesson 7: Move your data files to Azure Storage</span></span>](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
