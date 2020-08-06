---
title: 卸離和附加 DQS 資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3bcac9d1f53b10cf6356b878ce4006f66c198d99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592864"
---
# <a name="detaching-and-attaching-dqs-databases"></a><span data-ttu-id="8527c-102">卸離和附加 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="8527c-102">Detaching and Attaching DQS Databases</span></span>
  <span data-ttu-id="8527c-103">本主題描述如何卸離和附加 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8527c-103">This topic describes how to detach and attach the DQS databases.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8527c-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="8527c-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limitations"></a> <span data-ttu-id="8527c-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="8527c-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8527c-106">如需限制事項的清單，請參閱 [資料庫卸離與附加 &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md)中卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="8527c-106">For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="8527c-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="8527c-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="8527c-108">請確定 DQS 中沒有任何執行中的活動或處理序。</span><span class="sxs-lookup"><span data-stu-id="8527c-108">Ensure that there are no running activities or processes in DQS.</span></span> <span data-ttu-id="8527c-109">這可以使用 **[活動監控]** 畫面加以確認。</span><span class="sxs-lookup"><span data-stu-id="8527c-109">This can be verified using the **Activity Monitoring** screen.</span></span> <span data-ttu-id="8527c-110">如需有關在此畫面工作的詳細資訊，請參閱＜ [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8527c-110">For detailed information about working in this screen, see [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).</span></span>  
  
-   <span data-ttu-id="8527c-111">確定沒有任何使用者登入 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8527c-111">Ensure that there are no users logged on the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8527c-112">Security</span><span class="sxs-lookup"><span data-stu-id="8527c-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8527c-113">權限</span><span class="sxs-lookup"><span data-stu-id="8527c-113">Permissions</span></span>  
  
-   <span data-ttu-id="8527c-114">您的 Windows 使用者帳戶必須是 SQL Server 執行個體之 db_owner 固定伺服器角色的成員，才能卸離 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8527c-114">Your Windows user account must be a member of the db_owner fixed server role in the SQL Server instance to detach DQS databases.</span></span>  
  
-   <span data-ttu-id="8527c-115">您的 Windows 使用者帳戶必須擁有 CREATE DATABASE、CREATE ANY DATABASE 或 ALTER ANY DATABASE 權限，才能附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="8527c-115">Your Windows user account must have CREATE DATABASE, CREATE ANY DATABASE, or ALTER ANY DATABASE permission to attach a database.</span></span>  
  
-   <span data-ttu-id="8527c-116">您必須擁有 DQS_MAIN 資料庫的 dqs_administrator 角色，才能在 DQS 中終止任何執行中的活動或停止任何執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="8527c-116">You must have the dqs_administrator role on the DQS_MAIN database to terminate any running activities or stop any running processes in DQS.</span></span>  
  
##  <a name="detach-dqs-databases"></a><a name="Detach"></a><span data-ttu-id="8527c-117">卸離 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="8527c-117">Detach DQS Databases</span></span>  
 <span data-ttu-id="8527c-118">當您使用 SQL Server Management Studio 卸離 DQS 資料庫時，卸離的檔案仍會保留在您的電腦上，可供您將其重新附加至相同的 SQL Server 執行個體，或是移到另一部伺服器並附加至該處。</span><span class="sxs-lookup"><span data-stu-id="8527c-118">When you detach a DQS database using SQL Server Management Studio, the detached files remain on your computer, and can be reattached to the same SQL Server instance or can be can be moved to another server and attached there.</span></span> <span data-ttu-id="8527c-119">DQS 資料庫檔案通常位於 Data Quality Services 電腦上的下列位置： C:\Program Files\Microsoft SQL Server\MSSQL12。*<Instance_Name>* \mssql\data。</span><span class="sxs-lookup"><span data-stu-id="8527c-119">The DQS database files are typically available at the following location on your Data Quality Services computer: C:\Program Files\Microsoft SQL Server\MSSQL12.*<Instance_Name>* \MSSQL\DATA.</span></span>  
  
1.  <span data-ttu-id="8527c-120">啟動 Microsoft SQL Server Management Studio，並連接到適當的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8527c-120">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="8527c-121">在 [物件總管] 中，展開 **[資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="8527c-121">In Object Explorer, expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="8527c-122">以滑鼠右鍵按一下 **[DQS_MAIN]** 資料庫，並指向 **[工作]**，然後按一下 **[卸離]**。</span><span class="sxs-lookup"><span data-stu-id="8527c-122">Right-click the **DQS_MAIN** database, point to **Tasks**, and then click **Detach**.</span></span> <span data-ttu-id="8527c-123">**[卸離資料庫]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8527c-123">The **Detach Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="8527c-124">選取 **[卸除]** 資料行底下的核取方塊，然後按一下 **[確定]** 以卸離 DQS_MAIN 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8527c-124">Select the check box under the **Drop** column, and click **OK** to detach the DQS_MAIN database.</span></span>  
  
5.  <span data-ttu-id="8527c-125">針對 DQS_PROJECTS 及 DQS_STAGING_DATA 資料庫重複步驟 3 和 4 予以卸離。</span><span class="sxs-lookup"><span data-stu-id="8527c-125">Repeat steps 3 and 4 with the DQS_PROJECTS and DQS_STAGING_DATA databases to detach them.</span></span>  
  
 <span data-ttu-id="8527c-126">您也可以使用 Transact-SQL 陳述式，透過 sp_detach_db 預存程序卸離 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8527c-126">You can also detach DQS databases using the Transact-SQL statements by using the sp_detach_db stored procedure.</span></span> <span data-ttu-id="8527c-127">如需有關使用 Transact-SQL 陳述式卸離資料庫的詳細資訊，請參閱＜ [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) ＞中的＜ [Detach a Database](../relational-databases/databases/detach-a-database.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8527c-127">For more information about detaching databases using Transact-SQL statements, see [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) in [Detach a Database](../relational-databases/databases/detach-a-database.md).</span></span>  
  
##  <a name="attach-dqs-databases"></a><a name="Attach"></a><span data-ttu-id="8527c-128">附加 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="8527c-128">Attach DQS Databases</span></span>  
 <span data-ttu-id="8527c-129">請使用下列指示，將 DQS 資料庫附加至相同的 SQL Server 執行個體 (原本卸離之處) 或是 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 安裝所在的另一個 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8527c-129">Use the following instructions to attach a DQS database to the same SQL Server instance (from where you detached) or a different SQL Server instance where [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
1.  <span data-ttu-id="8527c-130">啟動 Microsoft SQL Server Management Studio，並連接到適當的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8527c-130">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="8527c-131">在 [物件總管] 中，以滑鼠右鍵按一下 **[資料庫]**，然後按一下 **[附加]**。</span><span class="sxs-lookup"><span data-stu-id="8527c-131">In Object Explorer, right-click **Databases**, and then click **Attach**.</span></span> <span data-ttu-id="8527c-132">**[附加資料庫]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8527c-132">The **Attach Databases** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="8527c-133">若要指定欲附加的資料庫，請按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="8527c-133">To specify the database to be attached, click **Add**.</span></span> <span data-ttu-id="8527c-134">**[尋找資料庫檔案]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8527c-134">The **Locate Database Files** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="8527c-135">選取資料庫所在的磁碟機、展開目錄樹狀結構，尋找並選取資料庫的 .mdf 檔案。</span><span class="sxs-lookup"><span data-stu-id="8527c-135">Select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database.</span></span> <span data-ttu-id="8527c-136">以 DQS_MAIN 資料庫為例：</span><span class="sxs-lookup"><span data-stu-id="8527c-136">For example, for the DQS_MAIN database:</span></span>  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.  <span data-ttu-id="8527c-137">**[資料庫詳細資料]** (下方) 窗格會顯示要附加之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="8527c-137">The **database details** (lower) pane displays the names of the files to be attached.</span></span> <span data-ttu-id="8527c-138">若要確認或變更檔案的路徑名稱，請按一下 [瀏覽] 按鈕 ( ... )。</span><span class="sxs-lookup"><span data-stu-id="8527c-138">To verify or change the pathname of a file, click the **Browse** button (...).</span></span>  
  
6.  <span data-ttu-id="8527c-139">按一下 **[確定]** 以附加 DQS_MAIN 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8527c-139">Click **OK** to attach the DQS_MAIN database.</span></span>  
  
7.  <span data-ttu-id="8527c-140">針對 DQS_PROJECTS 及 DQS_STAGING_DATA 資料庫重複步驟 2-6 予以附加。</span><span class="sxs-lookup"><span data-stu-id="8527c-140">Repeat steps 2-6 for the DQS_PROJECTS and DQS_STAGING_DATA databases to attach them.</span></span>  
  
8.  <span data-ttu-id="8527c-141">在您還原 DQS_MAIN 資料庫之後，還必須執行下一個步驟中的 Transact-SQL 陳述式，否則當您嘗試使用 Data Quality Client 應用程式連接到資料品質伺服器時，將會因為無法連接而出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8527c-141">You must also run the Transact-SQL statements in the next step after restoring the DQS_MAIN database otherwise an error message is displayed when you try to connect to Data Quality Server by using the Data Quality Client application, and you cannot connect.</span></span> <span data-ttu-id="8527c-142">但是，如果您只附加了 DQS_PROJECTS 或 DQS_STAGING_DATA 資料庫而非 DQS_MAIN，便不需要執行步驟 9 和 10。</span><span class="sxs-lookup"><span data-stu-id="8527c-142">However, you do not need to perform steps 9 and 10 if you have just attached the DQS_PROJECTS or DQS_STAGING_DATA database, and not DQS_MAIN.</span></span>  
  
     <span data-ttu-id="8527c-143">若要執行 Transact-SQL 陳述式，請在 [物件總管] 中以滑鼠右鍵按一下伺服器，然後按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="8527c-143">To run the Transact-SQL statements, in Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
9. <span data-ttu-id="8527c-144">在 [查詢編輯器] 視窗中，複製下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="8527c-144">In the Query Editor window, copy the following SQL statements:</span></span>  
  
    ```sql  
    ALTER DATABASE [DQS_MAIN] SET TRUSTWORTHY ON;  
    EXEC sp_configure 'clr enabled', 1;  
    RECONFIGURE WITH OVERRIDE  
    ALTER DATABASE [DQS_MAIN] SET ENABLE_BROKER  
    ALTER AUTHORIZATION ON DATABASE::[DQS_MAIN] TO [##MS_dqs_db_owner_login##]  
    ALTER AUTHORIZATION ON DATABASE::[DQS_PROJECTS] TO [##MS_dqs_db_owner_login##]  
    ```  
  
10. <span data-ttu-id="8527c-145">按 F5 執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="8527c-145">Press F5 to execute the statements.</span></span> <span data-ttu-id="8527c-146">檢查 [結果] 窗格，確認陳述式是否皆已成功地執行。</span><span class="sxs-lookup"><span data-stu-id="8527c-146">Check the Results pane to verify that the statements have executed successfully.</span></span> <span data-ttu-id="8527c-147">您將會看到下列訊息： `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`</span><span class="sxs-lookup"><span data-stu-id="8527c-147">You will see the following message: `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`</span></span>  
  
11. <span data-ttu-id="8527c-148">使用 Data Quality Client 連接到資料品質伺服器以確認能否順利連接。</span><span class="sxs-lookup"><span data-stu-id="8527c-148">Connect to the Data Quality Server using the Data Quality Client to verify if you can connect successfully.</span></span>  
  
 <span data-ttu-id="8527c-149">您也可以使用 Transact-SQL 陳述式附加 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8527c-149">You can also attach DQS databases using the Transact-SQL statements.</span></span> <span data-ttu-id="8527c-150">如需有關使用 Transact-SQL 陳述式附加資料庫的詳細資訊，請參閱＜ [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) ＞中的＜ [Attach a Database](../relational-databases/databases/attach-a-database.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8527c-150">For more information about attaching databases using Transact-SQL statements, see [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) in [Attach a Database](../relational-databases/databases/attach-a-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8527c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8527c-151">See Also</span></span>  
 [<span data-ttu-id="8527c-152">管理 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="8527c-152">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
