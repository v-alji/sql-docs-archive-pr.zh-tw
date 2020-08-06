---
title: 將檔案還原到新位置 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring files [SQL Server], how-to topics
- restoring databases [SQL Server], moving
- restoring files [SQL Server], steps
- file restores [SQL Server], how-to topics
- filegroups [SQL Server], restoring
- restoring filegroups [SQL Server]
ms.assetid: b4f4791d-646e-4632-9980-baae9cb1aade
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a8336e5d186fb72df4e0a17fdd9affccab4ee57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699796"
---
# <a name="restore-files-to-a-new-location-sql-server"></a><span data-ttu-id="32172-102">將檔案還原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="32172-102">Restore Files to a New Location (SQL Server)</span></span>
  <span data-ttu-id="32172-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中將檔案還原到新位置。</span><span class="sxs-lookup"><span data-stu-id="32172-103">This topic describes how to restore files to a new location in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="32172-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="32172-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="32172-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="32172-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="32172-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="32172-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="32172-107">安全性</span><span class="sxs-lookup"><span data-stu-id="32172-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="32172-108">**若要使用下列項目將檔案還原到新位置：**</span><span class="sxs-lookup"><span data-stu-id="32172-108">**To restore files to a new location, using:**</span></span>  
  
     [<span data-ttu-id="32172-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="32172-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="32172-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="32172-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="32172-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="32172-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="32172-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="32172-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="32172-113">負責還原檔案的系統管理員，必須是目前唯一正在使用即將還原之資料庫的人。</span><span class="sxs-lookup"><span data-stu-id="32172-113">The system administrator restoring the files must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="32172-114">在明確或隱含的交易中，不允許使用 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="32172-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="32172-115">在完整或大量記錄復原模式下，您必須先備份使用中的交易記錄 (也稱為記錄的結尾)，才能還原檔案。</span><span class="sxs-lookup"><span data-stu-id="32172-115">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="32172-116">如需詳細資訊，請參閱 [備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="32172-116">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="32172-117">若要還原加密的資料庫，您必須能夠存取之前用來加密資料庫的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="32172-117">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="32172-118">如果沒有該憑證或非對稱金鑰，就無法還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="32172-118">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="32172-119">因此，只要需要備份，就必須保留用來加密資料庫加密金鑰的憑證。</span><span class="sxs-lookup"><span data-stu-id="32172-119">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="32172-120">如需詳細資訊，請參閱 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="32172-120">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="32172-121">Security</span><span class="sxs-lookup"><span data-stu-id="32172-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="32172-122">權限</span><span class="sxs-lookup"><span data-stu-id="32172-122">Permissions</span></span>  
 <span data-ttu-id="32172-123">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="32172-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="32172-124">如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。</span><span class="sxs-lookup"><span data-stu-id="32172-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="32172-125">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="32172-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="32172-126">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="32172-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="32172-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="32172-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-to-a-new-location"></a><span data-ttu-id="32172-128">若要將檔案還原到新位置</span><span class="sxs-lookup"><span data-stu-id="32172-128">To restore files to a new location</span></span>  
  
1.  <span data-ttu-id="32172-129">在 [物件總管]  中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，展開該執行個體，然後展開 [資料庫]  。</span><span class="sxs-lookup"><span data-stu-id="32172-129">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="32172-130">以滑鼠右鍵按一下所要的資料庫，依序指向 [工作]  與 [還原]  ，然後按一下 [檔案與檔案群組]  。</span><span class="sxs-lookup"><span data-stu-id="32172-130">Right-click the database that you want, point to **Tasks**, point to **Restore**, and then click **Files and Filegroups**.</span></span>  
  
3.  <span data-ttu-id="32172-131">在 **[一般]** 頁面上的 **[目的地資料庫]** 清單方塊，輸入要還原的資料庫。</span><span class="sxs-lookup"><span data-stu-id="32172-131">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="32172-132">您可以輸入新的資料庫，或者從下拉式清單中選擇現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="32172-132">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="32172-133">清單包含伺服器上的所有資料庫，排除系統資料庫 **master** 和 **tempdb**。</span><span class="sxs-lookup"><span data-stu-id="32172-133">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
4.  <span data-ttu-id="32172-134">若要指定要還原之備份組的來源與位置，請按一下下列任一個選項：</span><span class="sxs-lookup"><span data-stu-id="32172-134">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="32172-135">**來源資料庫**</span><span class="sxs-lookup"><span data-stu-id="32172-135">**From database**</span></span>  
  
         <span data-ttu-id="32172-136">在清單方塊中輸入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-136">Enter a database name in the list box.</span></span> <span data-ttu-id="32172-137">此清單僅包含已根據 **msdb** 備份記錄而備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="32172-137">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="32172-138">**來源裝置**</span><span class="sxs-lookup"><span data-stu-id="32172-138">**From device**</span></span>  
  
         <span data-ttu-id="32172-139">按一下 [瀏覽] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="32172-139">Click the browse button.</span></span> <span data-ttu-id="32172-140">在 **[指定備份裝置]** 對話方塊中，選取 **[備份媒體類型]** 清單方塊上列出的其中一個裝置類型。</span><span class="sxs-lookup"><span data-stu-id="32172-140">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="32172-141">若要選取 **[備份媒體]** 清單方塊的一個或多個裝置，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="32172-141">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="32172-142">將您要的裝置加入 **[備份媒體]** 清單方塊後，按一下 **[確定]** 即可回到 **[一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="32172-142">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
5.  <span data-ttu-id="32172-143">在 **[選取要還原的備份組]** 方格中，選取要還原的備份。</span><span class="sxs-lookup"><span data-stu-id="32172-143">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="32172-144">這個方格會顯示指定位置可用的備份。</span><span class="sxs-lookup"><span data-stu-id="32172-144">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="32172-145">依預設，會建議一個復原計畫。</span><span class="sxs-lookup"><span data-stu-id="32172-145">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="32172-146">若要覆寫建議的復原計畫，您可以變更方格中的選取項目。</span><span class="sxs-lookup"><span data-stu-id="32172-146">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="32172-147">任何相依於已取消選取備份的備份，會自動被取消選取。</span><span class="sxs-lookup"><span data-stu-id="32172-147">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="32172-148">資料行標頭</span><span class="sxs-lookup"><span data-stu-id="32172-148">Column head</span></span>|<span data-ttu-id="32172-149">值</span><span class="sxs-lookup"><span data-stu-id="32172-149">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="32172-150">**Restore**</span><span class="sxs-lookup"><span data-stu-id="32172-150">**Restore**</span></span>|<span data-ttu-id="32172-151">選取的核取方塊會指出要還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="32172-151">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="32172-152">**名稱**</span><span class="sxs-lookup"><span data-stu-id="32172-152">**Name**</span></span>|<span data-ttu-id="32172-153">備份組的名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-153">The name of the backup set.</span></span>|  
    |<span data-ttu-id="32172-154">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="32172-154">**File Type**</span></span>|<span data-ttu-id="32172-155">指定備份中的資料類型：[資料]  、[記錄]  或 [Filestream 資料]  。</span><span class="sxs-lookup"><span data-stu-id="32172-155">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="32172-156">資料表中所包含的資料位於 **[資料]** 檔案中。</span><span class="sxs-lookup"><span data-stu-id="32172-156">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="32172-157">交易記錄資料位於 **[記錄檔]** 中。</span><span class="sxs-lookup"><span data-stu-id="32172-157">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="32172-158">儲存在檔案系統上的二進位大型物件 (BLOB) 資料位於 [Filestream 資料]  檔案中。</span><span class="sxs-lookup"><span data-stu-id="32172-158">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="32172-159">**型別**</span><span class="sxs-lookup"><span data-stu-id="32172-159">**Type**</span></span>|<span data-ttu-id="32172-160">執行的備份類型：[完整]、[差異] 或 [交易記錄]。</span><span class="sxs-lookup"><span data-stu-id="32172-160">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="32172-161">**Server**</span><span class="sxs-lookup"><span data-stu-id="32172-161">**Server**</span></span>|<span data-ttu-id="32172-162">執行備份作業的 Database Engine 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-162">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="32172-163">**檔案邏輯名稱**</span><span class="sxs-lookup"><span data-stu-id="32172-163">**File Logical Name**</span></span>|<span data-ttu-id="32172-164">檔案的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-164">The logical name of the file.</span></span>|  
    |<span data-ttu-id="32172-165">**Database**</span><span class="sxs-lookup"><span data-stu-id="32172-165">**Database**</span></span>|<span data-ttu-id="32172-166">備份作業中所含的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-166">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="32172-167">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="32172-167">**Start Date**</span></span>|<span data-ttu-id="32172-168">備份作業開始時的日期和時間，會出現在用戶端的地區設定中。</span><span class="sxs-lookup"><span data-stu-id="32172-168">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="32172-169">**完成日期**</span><span class="sxs-lookup"><span data-stu-id="32172-169">**Finish Date**</span></span>|<span data-ttu-id="32172-170">備份作業完成時的日期和時間，會出現在用戶端的地區設定中。</span><span class="sxs-lookup"><span data-stu-id="32172-170">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="32172-171">**大小**</span><span class="sxs-lookup"><span data-stu-id="32172-171">**Size**</span></span>|<span data-ttu-id="32172-172">備份組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="32172-172">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="32172-173">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="32172-173">**User Name**</span></span>|<span data-ttu-id="32172-174">執行備份作業的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-174">The name of the user who performed the backup operation.</span></span>|  
  
6.  <span data-ttu-id="32172-175">在 **[選取頁面]** 窗格中，按一下 **[選項]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="32172-175">In the **Select a page** pane, click the **Options** page.</span></span>  
  
7.  <span data-ttu-id="32172-176">在 **[將資料庫檔案還原為]** 方格中，為要移動的檔案指定新位置。</span><span class="sxs-lookup"><span data-stu-id="32172-176">In the **Restore database files as** grid, specify a new location for the file or files that you want to move.</span></span>  
  
    |<span data-ttu-id="32172-177">資料行標頭</span><span class="sxs-lookup"><span data-stu-id="32172-177">Column head</span></span>|<span data-ttu-id="32172-178">值</span><span class="sxs-lookup"><span data-stu-id="32172-178">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="32172-179">**原始檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="32172-179">**Original File Name**</span></span>|<span data-ttu-id="32172-180">來源備份檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="32172-180">The full path of a source backup file.</span></span>|  
    |<span data-ttu-id="32172-181">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="32172-181">**File Type**</span></span>|<span data-ttu-id="32172-182">指定備份中的資料類型：[資料]  、[記錄]  或 [Filestream 資料]  。</span><span class="sxs-lookup"><span data-stu-id="32172-182">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="32172-183">資料表中所包含的資料位於 **[資料]** 檔案中。</span><span class="sxs-lookup"><span data-stu-id="32172-183">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="32172-184">交易記錄資料位於 **[記錄檔]** 中。</span><span class="sxs-lookup"><span data-stu-id="32172-184">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="32172-185">儲存在檔案系統上的二進位大型物件 (BLOB) 資料位於 [Filestream 資料]  檔案中。</span><span class="sxs-lookup"><span data-stu-id="32172-185">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="32172-186">**還原成**</span><span class="sxs-lookup"><span data-stu-id="32172-186">**Restore As**</span></span>|<span data-ttu-id="32172-187">還原資料庫檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="32172-187">The full path of the database file to be restored.</span></span> <span data-ttu-id="32172-188">若要指定新的還原檔案，請按一下文字方塊並編輯建議的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-188">To specify a new restore file, click the text box and edit the suggested path and file name.</span></span> <span data-ttu-id="32172-189">變更 **[還原成]** 資料行中的路徑或檔案名稱相當於使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式中的 MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="32172-189">Changing the path or file name in the **Restore As** column is equivalent to using the MOVE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>|  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="32172-190">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="32172-190">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-to-a-new-location"></a><span data-ttu-id="32172-191">若要將檔案還原到新位置</span><span class="sxs-lookup"><span data-stu-id="32172-191">To restore files to a new location</span></span>  
  
1.  <span data-ttu-id="32172-192">選擇性執行 RESTORE FILELISTONLY 陳述式，以決定完整資料庫備份中之檔案的數目和名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-192">Optionally, execute the RESTORE FILELISTONLY statement to determine the number and names of the files in the full database backup.</span></span>  
  
2.  <span data-ttu-id="32172-193">執行 RESTORE DATABASE 陳述式以還原完整資料庫備份，請指定：</span><span class="sxs-lookup"><span data-stu-id="32172-193">Execute the RESTORE DATABASE statement to restore the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="32172-194">所要還原的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-194">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="32172-195">將要還原完整資料庫備份的來源備份裝置。</span><span class="sxs-lookup"><span data-stu-id="32172-195">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="32172-196">替要還原的每個檔案指定 MOVE 子句，將其還原到新位置上。</span><span class="sxs-lookup"><span data-stu-id="32172-196">The MOVE clause for each file to restore to a new location.</span></span>  
  
    -   <span data-ttu-id="32172-197">NORECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="32172-197">The NORECOVERY clause.</span></span>  
  
3.  <span data-ttu-id="32172-198">如果檔案在備份建立之後做過修改，則請執行 RESTORE LOG 陳述式以套用交易記錄備份，並指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="32172-198">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="32172-199">交易記錄檔要套用的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-199">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="32172-200">用於還原交易記錄備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="32172-200">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="32172-201">倘若在目前的交易記錄備份之後還有另一個交易記錄備份要套用，請指定 NORECOVERY 子句，否則請指定 RECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="32172-201">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="32172-202">您所套用的交易記錄備份必須涵蓋檔案和檔案群組備份的時間。</span><span class="sxs-lookup"><span data-stu-id="32172-202">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="32172-203">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32172-203">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="32172-204">此範例會將原本位於磁碟機 C 的兩個 `MyNwind` 資料庫的檔案還原到磁碟機 D 上的新位置。此外，也會套用兩個交易記錄檔，以將資料庫還原到目前的時間。</span><span class="sxs-lookup"><span data-stu-id="32172-204">This example restores two of the files for the `MyNwind` database that were originally located on Drive C to new locations on Drive D. Two transaction logs will also be applied to restore the database to the current time.</span></span> <span data-ttu-id="32172-205">`RESTORE FILELISTONLY` 陳述式是用來決定資料庫中所要還原的檔案數目及其邏輯與實體名稱。</span><span class="sxs-lookup"><span data-stu-id="32172-205">The `RESTORE FILELISTONLY` statement is used to determine the number and logical and physical names of the files in the database being restored.</span></span>  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
RESTORE FILELISTONLY  
   FROM MyNwind_1;  
-- Restore the files for MyNwind.  
RESTORE DATABASE MyNwind  
   FROM MyNwind_1  
   WITH NORECOVERY,  
   MOVE 'MyNwind_data_1' TO 'D:\MyData\MyNwind_data_1.mdf',   
   MOVE 'MyNwind_data_2' TO 'D:\MyData\MyNwind_data_2.ndf';  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="32172-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32172-206">See Also</span></span>  
 <span data-ttu-id="32172-207">[還原資料庫備份 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="32172-207">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="32172-208">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="32172-208">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="32172-209">[使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="32172-209">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="32172-210">還原檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32172-210">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
  
