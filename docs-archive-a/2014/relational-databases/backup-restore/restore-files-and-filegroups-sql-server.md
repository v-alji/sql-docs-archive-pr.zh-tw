---
title: 還原檔案和檔案群組 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restorefilesandfilegrps.general.f1
- sql12.swb.restorefilesandfilegrps.options.f1
- sql12.swb.bselectfilegrpsfiles.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], restoring files and filegroups
- restoring [SQL Server], files
ms.assetid: 72603b21-3065-4b56-8b01-11b707911b05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2576f1326cb50fa197b1623aaa1326d70137823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699802"
---
# <a name="restore-files-and-filegroups-sql-server"></a><span data-ttu-id="fac7e-102">還原檔案和檔案群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fac7e-102">Restore Files and Filegroups (SQL Server)</span></span>
  <span data-ttu-id="fac7e-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中還原檔案與檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fac7e-103">This topic describes how to restore files and filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="fac7e-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="fac7e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fac7e-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="fac7e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fac7e-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="fac7e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="fac7e-107">安全性</span><span class="sxs-lookup"><span data-stu-id="fac7e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fac7e-108">**若要使用下列項目還原檔案和檔案群組：**</span><span class="sxs-lookup"><span data-stu-id="fac7e-108">**To restore files and filegroups, using:**</span></span>  
  
     [<span data-ttu-id="fac7e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fac7e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fac7e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fac7e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fac7e-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="fac7e-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fac7e-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="fac7e-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fac7e-113">負責還原檔案與檔案群組備份的系統管理員，必須是目前唯一正在使用即將還原之資料庫的人。</span><span class="sxs-lookup"><span data-stu-id="fac7e-113">The system administrator restoring the files and filegroups must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="fac7e-114">在明確或隱含的交易中，不允許使用 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="fac7e-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="fac7e-115">在簡單復原模式之下，檔案必須屬於唯讀檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fac7e-115">Under the simple recovery model, the file must belong to a read-only filegroup.</span></span>  
  
-   <span data-ttu-id="fac7e-116">在完整或大量記錄復原模式下，您必須先備份使用中的交易記錄 (也稱為記錄的結尾)，才能還原檔案。</span><span class="sxs-lookup"><span data-stu-id="fac7e-116">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="fac7e-117">如需詳細資訊，請參閱 [備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-117">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="fac7e-118">若要還原加密的資料庫，您必須能夠存取之前用來加密資料庫的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="fac7e-118">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="fac7e-119">如果沒有該憑證或非對稱金鑰，就無法還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-119">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="fac7e-120">因此，只要需要備份，就必須保留用來加密資料庫加密金鑰的憑證。</span><span class="sxs-lookup"><span data-stu-id="fac7e-120">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="fac7e-121">如需詳細資訊，請參閱 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="fac7e-121">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fac7e-122">Security</span><span class="sxs-lookup"><span data-stu-id="fac7e-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fac7e-123">權限</span><span class="sxs-lookup"><span data-stu-id="fac7e-123">Permissions</span></span>  
 <span data-ttu-id="fac7e-124">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="fac7e-124">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="fac7e-125">如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。</span><span class="sxs-lookup"><span data-stu-id="fac7e-125">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="fac7e-126">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="fac7e-126">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="fac7e-127">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="fac7e-127">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fac7e-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fac7e-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-and-filegroups"></a><span data-ttu-id="fac7e-129">還原檔案和檔案群組</span><span class="sxs-lookup"><span data-stu-id="fac7e-129">To restore files and filegroups</span></span>  
  
1.  <span data-ttu-id="fac7e-130">連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，請在 [物件總管] 中按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="fac7e-130">After you connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="fac7e-131">展開 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="fac7e-131">Expand **Databases**.</span></span> <span data-ttu-id="fac7e-132">視資料庫而定，選取使用者資料庫，或者展開 [系統資料庫]  ，再選取系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-132">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="fac7e-133">以滑鼠右鍵按一下資料庫，指向 [工作]  ，然後按一下 [還原]  。</span><span class="sxs-lookup"><span data-stu-id="fac7e-133">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="fac7e-134">按一下 **[檔案和檔案群組]** ，開啟 **[還原檔案和檔案群組]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fac7e-134">Click **Files and Filegroups**, which opens the **Restore Files and Filegroups** dialog box.</span></span>  
  
5.  <span data-ttu-id="fac7e-135">在 **[一般]** 頁面上的 **[目的地資料庫]** 清單方塊，輸入要還原的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-135">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="fac7e-136">您可以輸入新的資料庫，或者從下拉式清單中選擇現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-136">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="fac7e-137">清單包含伺服器上的所有資料庫，排除系統資料庫 **master** 和 **tempdb**。</span><span class="sxs-lookup"><span data-stu-id="fac7e-137">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
6.  <span data-ttu-id="fac7e-138">若要指定要還原之備份組的來源與位置，請按一下下列任一個選項：</span><span class="sxs-lookup"><span data-stu-id="fac7e-138">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="fac7e-139">**來源資料庫**</span><span class="sxs-lookup"><span data-stu-id="fac7e-139">**From database**</span></span>  
  
         <span data-ttu-id="fac7e-140">在清單方塊中輸入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-140">Enter a database name in the list box.</span></span> <span data-ttu-id="fac7e-141">此清單僅包含已根據 **msdb** 備份記錄而備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-141">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="fac7e-142">**來源裝置**</span><span class="sxs-lookup"><span data-stu-id="fac7e-142">**From device**</span></span>  
  
         <span data-ttu-id="fac7e-143">按一下 [瀏覽] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fac7e-143">Click the browse button.</span></span> <span data-ttu-id="fac7e-144">在 **[指定備份裝置]** 對話方塊中，選取 **[備份媒體類型]** 清單方塊上列出的其中一個裝置類型。</span><span class="sxs-lookup"><span data-stu-id="fac7e-144">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="fac7e-145">若要選取 **[備份媒體]** 清單方塊的一個或多個裝置，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="fac7e-145">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="fac7e-146">將您要的裝置加入 **[備份媒體]** 清單方塊後，按一下 **[確定]** 即可回到 **[一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="fac7e-146">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
7.  <span data-ttu-id="fac7e-147">在 **[選取要還原的備份組]** 方格中，選取要還原的備份。</span><span class="sxs-lookup"><span data-stu-id="fac7e-147">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="fac7e-148">這個方格會顯示指定位置可用的備份。</span><span class="sxs-lookup"><span data-stu-id="fac7e-148">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="fac7e-149">依預設，會建議一個復原計畫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-149">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="fac7e-150">若要覆寫建議的復原計畫，您可以變更方格中的選取項目。</span><span class="sxs-lookup"><span data-stu-id="fac7e-150">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="fac7e-151">任何相依於已取消選取備份的備份，會自動被取消選取。</span><span class="sxs-lookup"><span data-stu-id="fac7e-151">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="fac7e-152">資料行標頭</span><span class="sxs-lookup"><span data-stu-id="fac7e-152">Column head</span></span>|<span data-ttu-id="fac7e-153">值</span><span class="sxs-lookup"><span data-stu-id="fac7e-153">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="fac7e-154">**Restore**</span><span class="sxs-lookup"><span data-stu-id="fac7e-154">**Restore**</span></span>|<span data-ttu-id="fac7e-155">選取的核取方塊會指出要還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="fac7e-155">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="fac7e-156">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fac7e-156">**Name**</span></span>|<span data-ttu-id="fac7e-157">備份組的名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-157">The name of the backup set.</span></span>|  
    |<span data-ttu-id="fac7e-158">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="fac7e-158">**File Type**</span></span>|<span data-ttu-id="fac7e-159">指定備份中的資料類型：[資料]  、[記錄]  或 [Filestream 資料]  。</span><span class="sxs-lookup"><span data-stu-id="fac7e-159">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="fac7e-160">資料表中所包含的資料位於 **[資料]** 檔案中。</span><span class="sxs-lookup"><span data-stu-id="fac7e-160">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="fac7e-161">交易記錄資料位於 **[記錄檔]** 中。</span><span class="sxs-lookup"><span data-stu-id="fac7e-161">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="fac7e-162">儲存在檔案系統上的二進位大型物件 (BLOB) 資料位於 [Filestream 資料]  檔案中。</span><span class="sxs-lookup"><span data-stu-id="fac7e-162">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="fac7e-163">**型別**</span><span class="sxs-lookup"><span data-stu-id="fac7e-163">**Type**</span></span>|<span data-ttu-id="fac7e-164">執行的備份類型：[完整]、[差異] 或 [交易記錄]。</span><span class="sxs-lookup"><span data-stu-id="fac7e-164">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="fac7e-165">**Server**</span><span class="sxs-lookup"><span data-stu-id="fac7e-165">**Server**</span></span>|<span data-ttu-id="fac7e-166">執行備份作業的 Database Engine 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-166">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="fac7e-167">**檔案邏輯名稱**</span><span class="sxs-lookup"><span data-stu-id="fac7e-167">**File Logical Name**</span></span>|<span data-ttu-id="fac7e-168">檔案的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-168">The logical name of the file.</span></span>|  
    |<span data-ttu-id="fac7e-169">**Database**</span><span class="sxs-lookup"><span data-stu-id="fac7e-169">**Database**</span></span>|<span data-ttu-id="fac7e-170">備份作業中所含的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-170">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="fac7e-171">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="fac7e-171">**Start Date**</span></span>|<span data-ttu-id="fac7e-172">備份作業開始時的日期和時間，會出現在用戶端的地區設定中。</span><span class="sxs-lookup"><span data-stu-id="fac7e-172">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="fac7e-173">**完成日期**</span><span class="sxs-lookup"><span data-stu-id="fac7e-173">**Finish Date**</span></span>|<span data-ttu-id="fac7e-174">備份作業完成時的日期和時間，會出現在用戶端的地區設定中。</span><span class="sxs-lookup"><span data-stu-id="fac7e-174">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="fac7e-175">**大小**</span><span class="sxs-lookup"><span data-stu-id="fac7e-175">**Size**</span></span>|<span data-ttu-id="fac7e-176">備份組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="fac7e-176">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="fac7e-177">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="fac7e-177">**User Name**</span></span>|<span data-ttu-id="fac7e-178">執行備份作業的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-178">The name of the user who performed the backup operation.</span></span>|  
  
8.  <span data-ttu-id="fac7e-179">若要檢視或選取進階選項，請按一下 **[選取頁面]** 窗格中的 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="fac7e-179">To view or select the advanced options, click **Options** in the **Select a page pane**.</span></span>  
  
9. <span data-ttu-id="fac7e-180">在 **[還原選項]** 面板中，您可以選擇下列任何選項 (如果情況適用)。</span><span class="sxs-lookup"><span data-stu-id="fac7e-180">In the **Restore options** panel, you can choose any of the following options, if appropriate for your situation.</span></span>  
  
     <span data-ttu-id="fac7e-181">**還原成檔案群組**</span><span class="sxs-lookup"><span data-stu-id="fac7e-181">**Restore as filegroup**</span></span>  
     <span data-ttu-id="fac7e-182">指出正在還原整個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fac7e-182">Indicates that an entire filegroup is being restored.</span></span>  
  
     <span data-ttu-id="fac7e-183">**覆寫現有的資料庫**</span><span class="sxs-lookup"><span data-stu-id="fac7e-183">**Overwrite the existing database**</span></span>  
     <span data-ttu-id="fac7e-184">指定還原作業應該覆寫任何現有的資料庫及其相關檔案，即使已經有另一個資料庫或檔案具有相同名稱也一樣。</span><span class="sxs-lookup"><span data-stu-id="fac7e-184">Specifies that the restore operation should overwrite any existing databases and their related files, even if another database or file already exists with the same name.</span></span>  
  
     <span data-ttu-id="fac7e-185">選取此選項相當於使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式的 REPLACE 選項。</span><span class="sxs-lookup"><span data-stu-id="fac7e-185">Selecting this option is equivalent to using the REPLACE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="fac7e-186">**還原每個備份之前先提示**</span><span class="sxs-lookup"><span data-stu-id="fac7e-186">**Prompt before restoring each backup**</span></span>  
     <span data-ttu-id="fac7e-187">在將每個備份組還原之前，會要求您確認。</span><span class="sxs-lookup"><span data-stu-id="fac7e-187">Asks you for confirmation before restoring each backup set.</span></span>  
  
     <span data-ttu-id="fac7e-188">您必須為不同的媒體集交換磁帶時，這個選項特別有用，例如當伺服器只有一個磁帶機時。</span><span class="sxs-lookup"><span data-stu-id="fac7e-188">This option is particularly useful where you must swap tapes for different media sets, such as when the server has one tape device.</span></span>  
  
     <span data-ttu-id="fac7e-189">**限制對還原資料庫的存取**</span><span class="sxs-lookup"><span data-stu-id="fac7e-189">**Restrict access to the restored database**</span></span>  
     <span data-ttu-id="fac7e-190">僅有 **db_owner**、 **dbcreator**或 **系統管理員**的成員可以使用還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-190">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
     <span data-ttu-id="fac7e-191">選取此選項相當於使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式的 RESTRICTED_USER 選項。</span><span class="sxs-lookup"><span data-stu-id="fac7e-191">Selecting this option is synonymous to using the RESTRICTED_USER option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
10. <span data-ttu-id="fac7e-192">另外，您也可以在 **[將資料庫檔案還原為]** 方格中為每個檔案指定新的還原目的地，以將資料庫還原到新的位置。</span><span class="sxs-lookup"><span data-stu-id="fac7e-192">Optionally, you can restore the database to a new location by specifying a new restore destination for each file in the **Restore database files as** grid.</span></span>  
  
    |<span data-ttu-id="fac7e-193">資料行標頭</span><span class="sxs-lookup"><span data-stu-id="fac7e-193">Column head</span></span>|<span data-ttu-id="fac7e-194">值</span><span class="sxs-lookup"><span data-stu-id="fac7e-194">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="fac7e-195">**原始檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="fac7e-195">**Original File Name**</span></span>|<span data-ttu-id="fac7e-196">來源備份檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="fac7e-196">The full path of a source backup file.</span></span>|  
    |<span data-ttu-id="fac7e-197">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="fac7e-197">**File Type**</span></span>|<span data-ttu-id="fac7e-198">指定備份中的資料類型：[資料]  、[記錄]  或 [Filestream 資料]  。</span><span class="sxs-lookup"><span data-stu-id="fac7e-198">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="fac7e-199">資料表中所包含的資料位於 **[資料]** 檔案中。</span><span class="sxs-lookup"><span data-stu-id="fac7e-199">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="fac7e-200">交易記錄資料位於 **[記錄檔]** 中。</span><span class="sxs-lookup"><span data-stu-id="fac7e-200">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="fac7e-201">儲存在檔案系統上的二進位大型物件 (BLOB) 資料位於 [Filestream 資料]  檔案中。</span><span class="sxs-lookup"><span data-stu-id="fac7e-201">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="fac7e-202">**還原成**</span><span class="sxs-lookup"><span data-stu-id="fac7e-202">**Restore As**</span></span>|<span data-ttu-id="fac7e-203">還原資料庫檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="fac7e-203">The full path of the database file to be restored.</span></span> <span data-ttu-id="fac7e-204">若要指定新的還原檔案，請按一下文字方塊並編輯建議的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-204">To specify a new restore file, click the text box and edit the suggested path and file name.</span></span> <span data-ttu-id="fac7e-205">變更 **[還原成]** 資料行中的路徑或檔案名稱相當於使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式中的 MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="fac7e-205">Changing the path or file name in the **Restore As** column is equivalent to using the MOVE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>|  
  
11. <span data-ttu-id="fac7e-206">**[復原狀態]** 面板可決定資料庫在還原作業之後的狀態。</span><span class="sxs-lookup"><span data-stu-id="fac7e-206">The **Recovery state** panel determines the state of the database after the restore operation.</span></span>  
  
     <span data-ttu-id="fac7e-207">**回復未認可的交易，讓資料庫保持備妥可用。無法還原其他交易記錄。(RESTORE WITH RECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="fac7e-207">**Leave the database ready for use by rolling back the uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**</span></span>  
     <span data-ttu-id="fac7e-208">復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="fac7e-208">Recovers the database.</span></span> <span data-ttu-id="fac7e-209">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="fac7e-209">This is the default behavior.</span></span> <span data-ttu-id="fac7e-210">只有在您要立即還原所有必要的備份時，才選擇這個選項。</span><span class="sxs-lookup"><span data-stu-id="fac7e-210">Choose this option only if you are restoring all of the necessary backups now.</span></span> <span data-ttu-id="fac7e-211">此選項相當於在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式中指定 WITH RECOVERY。</span><span class="sxs-lookup"><span data-stu-id="fac7e-211">This option is equivalent to specifying WITH RECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="fac7e-212">**讓資料庫保持不運作，且不回復未認可的交易。可以還原其他交易記錄。(RESTORE WITH NORECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="fac7e-212">**Leave the database non-operational, and don't roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**</span></span>  
     <span data-ttu-id="fac7e-213">讓資料庫保持在還原狀態。</span><span class="sxs-lookup"><span data-stu-id="fac7e-213">Leaves the database in the restoring state.</span></span> <span data-ttu-id="fac7e-214">若要復原資料庫，就必須使用先前的 RESTORE WITH RECOVERY 選項 (請參閱上面說明) 執行另一個還原。</span><span class="sxs-lookup"><span data-stu-id="fac7e-214">To recover the database, you will need to perform another restore using the preceding RESTORE WITH RECOVERY option (see above).</span></span> <span data-ttu-id="fac7e-215">此選項相當於在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式中指定 WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="fac7e-215">This option is equivalent to specifying WITH NORECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="fac7e-216">如果選取此選項，將無法使用 **[保留複寫設定]** 選項。</span><span class="sxs-lookup"><span data-stu-id="fac7e-216">If you select this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
     <span data-ttu-id="fac7e-217">**讓資料庫保持唯讀模式。回復未認可的交易，但是將回復作業儲存在檔案中，以便能夠恢復復原結果。(RESTORE WITH STANDBY)**</span><span class="sxs-lookup"><span data-stu-id="fac7e-217">**Leave the database in read-only mode. Roll back the uncommitted transactions, but save the rollback operation in a file so the recovery effects can be undone. (RESTORE WITH STANDBY)**</span></span>  
     <span data-ttu-id="fac7e-218">讓資料庫處於待命狀態。</span><span class="sxs-lookup"><span data-stu-id="fac7e-218">Leaves the database in a standby state.</span></span> <span data-ttu-id="fac7e-219">此選項相當於在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式中指定 WITH STANDBY。</span><span class="sxs-lookup"><span data-stu-id="fac7e-219">This option is equivalent to specifying WITH STANDBY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="fac7e-220">您必須指定待命資料庫檔案，才能選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="fac7e-220">Choosing this option requires that you specify a standby file.</span></span>  
  
     <span data-ttu-id="fac7e-221">**回復恢復檔案**</span><span class="sxs-lookup"><span data-stu-id="fac7e-221">**Rollback undo file**</span></span>  
     <span data-ttu-id="fac7e-222">在 [回復恢復檔案]  文字方塊中，指定待命資料庫檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-222">Specify a standby file name in the **Rollback undo file** text box.</span></span> <span data-ttu-id="fac7e-223">如果您讓資料庫保持唯讀模式 (RESTORE WITH STANDBY)，就需要指定此選項。</span><span class="sxs-lookup"><span data-stu-id="fac7e-223">This option is required if you leave the database in read-only mode (RESTORE WITH STANDBY).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fac7e-224">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fac7e-224">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-and-filegroups"></a><span data-ttu-id="fac7e-225">還原檔案和檔案群組</span><span class="sxs-lookup"><span data-stu-id="fac7e-225">To restore files and filegroups</span></span>  
  
1.  <span data-ttu-id="fac7e-226">執行 RESTORE DATABASE 陳述式以還原檔案及檔案群組備份，並指定以下項目：</span><span class="sxs-lookup"><span data-stu-id="fac7e-226">Execute the RESTORE DATABASE statement to restore the file and filegroup backup, specifying:</span></span>  
  
    -   <span data-ttu-id="fac7e-227">所要還原的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-227">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="fac7e-228">將要還原完整資料庫備份的來源備份裝置。</span><span class="sxs-lookup"><span data-stu-id="fac7e-228">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="fac7e-229">替要還原的每個檔案指定 FILE 子句。</span><span class="sxs-lookup"><span data-stu-id="fac7e-229">The FILE clause for each file to restore.</span></span>  
  
    -   <span data-ttu-id="fac7e-230">替要還原的每個檔案群組指定 FILEGROUP 子句。</span><span class="sxs-lookup"><span data-stu-id="fac7e-230">The FILEGROUP clause for each filegroup to restore.</span></span>  
  
    -   <span data-ttu-id="fac7e-231">NORECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="fac7e-231">The NORECOVERY clause.</span></span> <span data-ttu-id="fac7e-232">如果檔案在備份建立之後沒有做過任何修改，請指定 RECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="fac7e-232">If the files have not been modified after the backup was created, specify the RECOVERY clause.</span></span>  
  
2.  <span data-ttu-id="fac7e-233">如果檔案在備份建立之後做過修改，則請執行 RESTORE LOG 陳述式以套用交易記錄備份，並指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="fac7e-233">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="fac7e-234">交易記錄檔要套用的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="fac7e-234">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="fac7e-235">用於還原交易記錄備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="fac7e-235">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="fac7e-236">倘若在目前的交易記錄備份之後還有另一個交易記錄備份要套用，請指定 NORECOVERY 子句，否則請指定 RECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="fac7e-236">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="fac7e-237">如果套用交易記錄備份，則交易記錄備份必須涵蓋備份檔案與檔案群組直到記錄結束的時間 (除非還原「所有的」資料庫檔案)。</span><span class="sxs-lookup"><span data-stu-id="fac7e-237">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up until the end of log (unless ALL database files are restored).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="fac7e-238">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fac7e-238">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="fac7e-239">這個範例會還原 `MyDatabase` 資料庫的檔案和檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fac7e-239">This example restores the files and filegroups for the `MyDatabase` database.</span></span> <span data-ttu-id="fac7e-240">為了將資料庫還原到目前的時間，還套用了兩份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="fac7e-240">To restore the database to the current time, two transaction logs are applied.</span></span>  
  
```sql  
USE master;  
GO  
-- Restore the files and filesgroups for MyDatabase.  
RESTORE DATABASE MyDatabase  
   FILE = 'MyDatabase_data_1',  
   FILEGROUP = 'new_customers',  
   FILE = 'MyDatabase_data_2',  
   FILEGROUP = 'first_qtr_sales'  
   FROM MyDatabase_1  
   WITH NORECOVERY;  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="fac7e-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fac7e-241">See Also</span></span>  
 <span data-ttu-id="fac7e-242">[還原資料庫備份 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="fac7e-242">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="fac7e-243">[備份檔案和檔案群組 &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fac7e-243">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="fac7e-244">[建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fac7e-244">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="fac7e-245">[備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fac7e-245">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="fac7e-246">[還原交易記錄備份 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fac7e-246">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="fac7e-247">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fac7e-247">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
