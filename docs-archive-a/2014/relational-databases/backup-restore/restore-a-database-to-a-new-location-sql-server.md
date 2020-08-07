---
title: 將資料庫還原到新位置 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], moving
- database restores [SQL Server], creating new databases
- restoring [SQL Server], with move
- restoring databases [SQL Server], creating new databases
- database backups [SQL Server], creating new database from
- backing up databases [SQL Server], creating new database from
- restoring databases [SQL Server], renaming
- database creation [SQL Server], restoring with move
ms.assetid: 4da76d61-5e11-4bee-84f5-b305240d9f42
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 89b42f439b5622074327506b9f2ca2b2358cd12f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598468"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a><span data-ttu-id="1dbbb-102">將資料庫還原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1dbbb-102">Restore a Database to a New Location (SQL Server)</span></span>
  <span data-ttu-id="1dbbb-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中將 [!INCLUDE[tsql](../../includes/tsql-md.md)]資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-103">This topic describes how to restore a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a new location, and optionally rename the database, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1dbbb-104">您可以將資料庫移至新目錄路徑，或是在相同的伺服器執行個體或不同的伺服器執行個體上建立資料庫的複本。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-104">You can move a database to a new directory path or create a copy of a database on either the same server instance or a different server instance.</span></span>  
  
 <span data-ttu-id="1dbbb-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1dbbb-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1dbbb-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1dbbb-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1dbbb-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="1dbbb-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1dbbb-108">先決條件</span><span class="sxs-lookup"><span data-stu-id="1dbbb-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="1dbbb-109">建議</span><span class="sxs-lookup"><span data-stu-id="1dbbb-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="1dbbb-110">安全性</span><span class="sxs-lookup"><span data-stu-id="1dbbb-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1dbbb-111">**若要使用下列項目將資料庫還原至新位置，並選擇性地重新命名資料庫：**</span><span class="sxs-lookup"><span data-stu-id="1dbbb-111">**To restore a database to a new location, and optionally rename the database, using:**</span></span>  
  
     [<span data-ttu-id="1dbbb-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1dbbb-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1dbbb-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1dbbb-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="1dbbb-114">相關工作</span><span class="sxs-lookup"><span data-stu-id="1dbbb-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1dbbb-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="1dbbb-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1dbbb-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="1dbbb-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1dbbb-117">負責還原完整資料庫備份的系統管理員，必須是目前唯一正在使用即將還原之資料庫的人員。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-117">The system administrator restoring a full database backup must be the only person currently using the database to be restored.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="1dbbb-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="1dbbb-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="1dbbb-119">在完整或大量記錄復原模式下，您必須先備份使用中交易記錄，才能還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-119">Under the full or bulk-logged recovery model, before you can restore a database, you must back up the active transaction log.</span></span> <span data-ttu-id="1dbbb-120">如需詳細資訊，請參閱 [備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-120">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1dbbb-121">建議</span><span class="sxs-lookup"><span data-stu-id="1dbbb-121">Recommendations</span></span>  
  
-   <span data-ttu-id="1dbbb-122">若要還原加密的資料庫，您必須能夠存取之前用來加密資料庫的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-122">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="1dbbb-123">如果沒有該憑證或非對稱金鑰，就無法還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-123">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="1dbbb-124">因此，只要需要備份，就必須保留用來加密資料庫加密金鑰的憑證。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-124">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="1dbbb-125">如需詳細資訊，請參閱 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-125">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
-   <span data-ttu-id="1dbbb-126">如需其他資料庫移動考量的相關資訊，請參閱[使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-126">For information about additional considerations for moving a database, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
-   <span data-ttu-id="1dbbb-127">如果您將 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本的資料庫還原成 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，資料庫會自動升級。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-127">If you restore a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or higher  database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is automatically upgraded.</span></span> <span data-ttu-id="1dbbb-128">通常，資料庫立即變為可用。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-128">Typically, the database becomes available immediately.</span></span> <span data-ttu-id="1dbbb-129">不過，如果 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 資料庫具有全文檢索索引，升級程序就會根據  **upgrade_option** 伺服器屬性的設定，匯入、重設或重建這些索引。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-129">However, if a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade_option** server property.</span></span> <span data-ttu-id="1dbbb-130">如果升級選項設定為匯入 (**upgrade_option** = 2) 或重建 (**upgrade_option** = 0)，則全文檢索索引在升級期間將無法使用。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-130">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="1dbbb-131">根據進行索引的資料數量而定，匯入可能需要數個小時，而重建可能需要十倍以上的時間。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-131">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="1dbbb-132">此外，請注意，當升級選項設定為 [匯入] 時，如果全文檢索目錄無法使用，系統就會重建相關聯的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-132">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="1dbbb-133">若要變更 **upgrade_option** 伺服器屬性的設定，請使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-133">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1dbbb-134">Security</span><span class="sxs-lookup"><span data-stu-id="1dbbb-134">Security</span></span>  
 <span data-ttu-id="1dbbb-135">基於安全性的理由，建議您不要附加或還原來源不明或來源不受信任的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-135">For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="1dbbb-136">這種資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-136">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="1dbbb-137">使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-137">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1dbbb-138">權限</span><span class="sxs-lookup"><span data-stu-id="1dbbb-138">Permissions</span></span>  
 <span data-ttu-id="1dbbb-139">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-139">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="1dbbb-140">如果資料庫存在，則 RESTORE 權限預設為 **系統管理員** 和 **dbcreator** 固定伺服器角色的成員，以及資料庫的擁有者 (**dbo**)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-140">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database.</span></span>  
  
 <span data-ttu-id="1dbbb-141">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-141">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="1dbbb-142">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-142">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1dbbb-143">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1dbbb-143">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a><span data-ttu-id="1dbbb-144">若要將資料庫還原至新位置，並選擇性地重新命名資料庫</span><span class="sxs-lookup"><span data-stu-id="1dbbb-144">To restore a database to a new location, and optionally rename the database</span></span>  
  
1.  <span data-ttu-id="1dbbb-145">連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體，然後在 [物件總管] 中，按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-145">Connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="1dbbb-146">以滑鼠右鍵按一下 [資料庫]  ，然後按一下 [還原資料庫]  。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-146">Right-click **Databases**, and then click **Restore Database**.</span></span> <span data-ttu-id="1dbbb-147">**[還原資料庫]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-147">The **Restore Database** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="1dbbb-148">在 **[一般]** 頁面上，使用 **[來源]** 區段指定要還原之備份組的來源和位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-148">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="1dbbb-149">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="1dbbb-149">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="1dbbb-150">**Database**</span><span class="sxs-lookup"><span data-stu-id="1dbbb-150">**Database**</span></span>  
  
         <span data-ttu-id="1dbbb-151">從下拉式清單中選取要還原的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-151">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="1dbbb-152">此清單僅包含已根據 **msdb** 備份記錄而備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-152">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1dbbb-153">如果備份是根據不同的伺服器建立的，目的地伺服器就沒有指定之資料庫的備份記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-153">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="1dbbb-154">在此情況下，請選取 **[裝置]** ，以便手動指定要還原的檔案或裝置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-154">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    1.  <span data-ttu-id="1dbbb-155">**裝置**</span><span class="sxs-lookup"><span data-stu-id="1dbbb-155">**Device**</span></span>  
  
         <span data-ttu-id="1dbbb-156">按一下瀏覽 ( **...** ) 按鈕，開啟 [選取備份裝置]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-156">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="1dbbb-157">在 **[備份媒體類型]** 方塊中，選取列出的其中一種裝置類型。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-157">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="1dbbb-158">若要選取 **[備份媒體]** 方塊中的一個或多個裝置，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-158">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="1dbbb-159">將您要的裝置加入 **[備份媒體]** 清單方塊後，按一下 **[確定]** 即可回到 **[一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-159">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="1dbbb-160">在 **[來源：裝置：資料庫]** 清單方塊中，選取應該還原的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-160">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="1dbbb-161">**注意** ：這份清單只能在選取 **[裝置]** 時使用。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-161">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="1dbbb-162">只有在所選取裝置上有備份的資料庫才可供使用。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-162">Only databases that have backups on the selected device will be available.</span></span>  
  
4.  <span data-ttu-id="1dbbb-163">在 **[目的地]** 區段中，會將要還原之資料庫的名稱自動填入 **[資料庫]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-163">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="1dbbb-164">若要變更資料庫的名稱，請在 **[資料庫]** 方塊中輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-164">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
5.  <span data-ttu-id="1dbbb-165">在 **[還原至]** 方塊中，保留 **[到上次建立的備份]** 預設值，或按一下 **[時間表]** 存取 **[備份時間表]** 對話方塊，手動選取停止復原動作的時間點。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-165">In the **Restore to** box, leave the default as **To the last backup taken** or click on **Timeline** to access the **Backup Timeline** dialog box to manually select a point in time to stop the recovery action.</span></span> <span data-ttu-id="1dbbb-166">如需有關指定特定時間點的詳細資訊，請參閱＜ [Backup Timeline](backup-timeline.md) ＞。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-166">See [Backup Timeline](backup-timeline.md) for more information on designating a specific point in time.</span></span>  
  
6.  <span data-ttu-id="1dbbb-167">在 **[要還原的備份組]** 方格中，選取要還原的備份。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-167">In the **Backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="1dbbb-168">這個方格會顯示指定位置可用的備份。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-168">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="1dbbb-169">依預設，會建議一個復原計畫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-169">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="1dbbb-170">若要覆寫建議的復原計畫，您可以變更方格中的選取項目。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-170">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="1dbbb-171">取消選取先前的備份時，會自動取消選取相依於先前備份還原的備份。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-171">Backups that depend on the restoration of an earlier backup are automatically deselected when the earlier backup is deselected.</span></span>  
  
     <span data-ttu-id="1dbbb-172">如需 [要還原的備份組]  方格中各資料行的相關資訊，請參閱[還原資料庫 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-172">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
7.  <span data-ttu-id="1dbbb-173">若要指定資料庫檔案的新位置，請選取 **[檔案]** 頁面，然後按一下 **[將所有檔案重新放置到資料夾]** 。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-173">To specify the new location of the database files, select the **Files** page, and then click **Relocate all files to folder**.</span></span> <span data-ttu-id="1dbbb-174">提供 **[資料檔資料夾]** 及 **[記錄檔資料夾]** 的新位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-174">Provide a new location for the **Data file folder** and **Log file folder**.</span></span> <span data-ttu-id="1dbbb-175">如需這個方格的詳細資訊，請參閱[還原資料庫 &#40;檔案頁面&#41;](restore-database-files-page.md)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-175">For more information about this grid, see [Restore Database &#40;Files Page&#41;](restore-database-files-page.md).</span></span>  
  
8.  <span data-ttu-id="1dbbb-176">在 **[選項]** 頁面上，依需要調整選項。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-176">On the **Options** page, adjust the options if you want.</span></span> <span data-ttu-id="1dbbb-177">如需這些選項的詳細資訊，請參閱[還原資料庫 &#40;選項頁面&#41;](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-177">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1dbbb-178">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1dbbb-178">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a><span data-ttu-id="1dbbb-179">若要將資料庫還原至新位置，並選擇性地重新命名資料庫</span><span class="sxs-lookup"><span data-stu-id="1dbbb-179">To restore a database to a new location, and optionally rename the database</span></span>  
  
1.  <span data-ttu-id="1dbbb-180">(選擇性) 在包含您想要還原之完整資料庫備份的備份組中，決定檔案的邏輯和實體名稱。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-180">Optionally, determine the logical and physical names of the files in the backup set that contains the full database backup that you want to restore.</span></span> <span data-ttu-id="1dbbb-181">這個陳述式會傳回備份組內所自主資料庫和記錄檔清單。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-181">This statement returns a list of the database and log files contained in the backup set.</span></span> <span data-ttu-id="1dbbb-182">基本語法如下：</span><span class="sxs-lookup"><span data-stu-id="1dbbb-182">The basic syntax is as follows:</span></span>  
  
     <span data-ttu-id="1dbbb-183">RESTORE FILELISTONLY FROM <備份裝置>  WITH FILE = *backup_set_file_number*</span><span class="sxs-lookup"><span data-stu-id="1dbbb-183">RESTORE FILELISTONLY FROM *<backup_device>* WITH FILE = *backup_set_file_number*</span></span>  
  
     <span data-ttu-id="1dbbb-184">此處，*backup_set_file_number* 表示媒體集中的備份位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-184">Here, *backup_set_file_number* indicates the position of the backup in the media set.</span></span> <span data-ttu-id="1dbbb-185">您可以使用 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 陳述式來取得備份組的位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-185">You can obtain the position of a backup set by using the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span> <span data-ttu-id="1dbbb-186">如需詳細資訊，請參閱 [RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 中的＜指定備份組＞。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-186">For more information, see "Specifying a Backup Set" in [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
     <span data-ttu-id="1dbbb-187">這個陳述式也支援一些 WITH 選項。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-187">This statement also supports a number of WITH options.</span></span> <span data-ttu-id="1dbbb-188">如需詳細資訊，請參閱 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-188">For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>  
  
2.  <span data-ttu-id="1dbbb-189">使用 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式來還原完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-189">Use the [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) statement to restore the full database backup.</span></span> <span data-ttu-id="1dbbb-190">根據預設，資料和記錄檔會還原到其原始位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-190">By default, data and log files are restored to their original locations.</span></span> <span data-ttu-id="1dbbb-191">若要重新放置資料庫，請使用 MOVE 選項來重新放置每個資料庫檔案，避免與現有的檔案發生衝突。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-191">To relocate a database, use the MOVE option to relocate each of the database files and to avoid collisions with existing files.</span></span>  
  
     <span data-ttu-id="1dbbb-192">將資料庫還原至新位置和新名稱的基本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法為：</span><span class="sxs-lookup"><span data-stu-id="1dbbb-192">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for restoring the database to a new location and a new name is:</span></span>  
  
     <span data-ttu-id="1dbbb-193">RESTORE DATABASE *new_database_name*</span><span class="sxs-lookup"><span data-stu-id="1dbbb-193">RESTORE DATABASE *new_database_name*</span></span>  
  
     <span data-ttu-id="1dbbb-194">FROM *backup_device* [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1dbbb-194">FROM *backup_device* [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="1dbbb-195">[ WITH</span><span class="sxs-lookup"><span data-stu-id="1dbbb-195">[ WITH</span></span>  
  
     <span data-ttu-id="1dbbb-196">{</span><span class="sxs-lookup"><span data-stu-id="1dbbb-196">{</span></span>  
  
     <span data-ttu-id="1dbbb-197">[**修復**|NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="1dbbb-197">[ **RECOVERY** | NORECOVERY ]</span></span>  
  
     <span data-ttu-id="1dbbb-198">[ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]</span><span class="sxs-lookup"><span data-stu-id="1dbbb-198">[ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]</span></span>  
  
     <span data-ttu-id="1dbbb-199">[ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1dbbb-199">[ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="1dbbb-200">}</span><span class="sxs-lookup"><span data-stu-id="1dbbb-200">}</span></span>  
  
     <span data-ttu-id="1dbbb-201">;</span><span class="sxs-lookup"><span data-stu-id="1dbbb-201">;</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1dbbb-202">準備要在不同的磁碟上重新放置資料庫時，您應該確認有足夠的可用空間，並且識別與現有檔案發生衝突的任何可能性。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-202">When preparing to relocate a database on a different disk, you should verify that sufficient space is available and identify any potential collisions with existing files.</span></span> <span data-ttu-id="1dbbb-203">這項作業包括使用 [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) 陳述式，其中指定您打算在 RESTORE DATABASE 陳述式中使用的相同 MOVE 參數。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-203">This involves using a [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) statement that specifies the same MOVE parameters that you plan to use in your RESTORE DATABASE statement.</span></span>  
  
     <span data-ttu-id="1dbbb-204">下表針對將資料庫還原到新位置的作業，描述這個 RESTORE 陳述式的引數。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-204">The following table describes arguments of this RESTORE statement in terms of restoring a database to a new location.</span></span> <span data-ttu-id="1dbbb-205">如需這些引數的詳細資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-205">For more information about these arguments, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
     <span data-ttu-id="1dbbb-206">*new_database_name*</span><span class="sxs-lookup"><span data-stu-id="1dbbb-206">*new_database_name*</span></span>  
     <span data-ttu-id="1dbbb-207">資料庫的新名稱。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-207">The new name for the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1dbbb-208">如果您要將資料庫還原至不同的伺服器執行個體，可以使用原始資料庫名稱而非新名稱。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-208">If you are restoring the database to a different server instance, you can use the original database name instead of a new name.</span></span>  
  
     <span data-ttu-id="1dbbb-209">*backup_device* [ `,` ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1dbbb-209">*backup_device* [ `,`...*n* ]</span></span>  
     <span data-ttu-id="1dbbb-210">指定一份逗號分隔清單，其中列出要從中還原資料庫備份的 1 到 64 個備份裝置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-210">Specifies a comma-separated list of from 1 to 64 backup devices from which the database backup is to be restored.</span></span> <span data-ttu-id="1dbbb-211">您可以指定實體備份裝置，也可以指定對應的邏輯備份裝置 (如果已定義的話)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-211">You can specify a physical backup device, or you can specify a corresponding logical backup device, if defined.</span></span> <span data-ttu-id="1dbbb-212">若要指定實體備份裝置，請使用 DISK 或 TAPE 選項：</span><span class="sxs-lookup"><span data-stu-id="1dbbb-212">To specify a physical backup device, use the DISK or TAPE option:</span></span>  
  
     <span data-ttu-id="1dbbb-213">{ DISK | TAPE } `=` *physical_backup_device_name*</span><span class="sxs-lookup"><span data-stu-id="1dbbb-213">{ DISK | TAPE } `=`*physical_backup_device_name*</span></span>  
  
     <span data-ttu-id="1dbbb-214">如需詳細資訊，請參閱 [備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md)執行個體上建立資料庫備份，就需要這個選項。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-214">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
     <span data-ttu-id="1dbbb-215">{ **RECOVERY** | NORECOVERY }</span><span class="sxs-lookup"><span data-stu-id="1dbbb-215">{ **RECOVERY** | NORECOVERY }</span></span>  
     <span data-ttu-id="1dbbb-216">如果資料庫使用完整復原模式，您可能必須在還原資料庫之後套用交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-216">If the database uses the full recovery model, you might need to apply transaction log backups after you restore the database.</span></span> <span data-ttu-id="1dbbb-217">在此情況下，請指定 NORECOVERY 選項。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-217">In this case, specify the NORECOVERY option.</span></span>  
  
     <span data-ttu-id="1dbbb-218">否則，請使用 RECOVERY 選項 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-218">Otherwise, use the RECOVERY option, which is the default.</span></span>  
  
     <span data-ttu-id="1dbbb-219">FILE = { *backup_set_file_number* | @*backup_set_file_number* }</span><span class="sxs-lookup"><span data-stu-id="1dbbb-219">FILE = { *backup_set_file_number* | @*backup_set_file_number* }</span></span>  
     <span data-ttu-id="1dbbb-220">識別要還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-220">Identifies the backup set to be restored.</span></span> <span data-ttu-id="1dbbb-221">例如， *backup_set_file_number* 為 **1** ，表示備份媒體的第一個備份組； *backup_set_file_number* 為 **2** ，表示第二個備份組。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-221">For example, a *backup_set_file_number* of **1** indicates the first backup set on the backup medium and a *backup_set_file_number* of **2** indicates the second backup set.</span></span> <span data-ttu-id="1dbbb-222">您可以使用 *RESTORE HEADERONLY* 陳述式來取得備份組的 [backup_set_file_number](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-222">You can obtain the *backup_set_file_number* of a backup set by using the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="1dbbb-223">沒有指定這個選項時，預設值是使用備份裝置上的第一個備份組。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-223">When this option is not specified, the default is to use the first backup set on the backup device.</span></span>  
  
     <span data-ttu-id="1dbbb-224">如需詳細資訊，請參閱 [RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 中的＜指定備份組＞。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-224">For more information, see "Specifying a Backup Set," in [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
     <span data-ttu-id="1dbbb-225">將 **' *`logical_file_name_in_backup`* '** 移至 **' *`operating_system_file_name`* '** [ `,` .。。*n* ]</span><span class="sxs-lookup"><span data-stu-id="1dbbb-225">MOVE **'*`logical_file_name_in_backup`*'** TO **'*`operating_system_file_name`*'** [ `,`...*n* ]</span></span>  
     <span data-ttu-id="1dbbb-226">指定 *logical_file_name_in_backup* 所指定的資料或記錄檔要還原至 *operating_system_file_name*所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-226">Specifies that the data or log file specified by *logical_file_name_in_backup* is to be restored to the location specified by *operating_system_file_name*.</span></span> <span data-ttu-id="1dbbb-227">針對您想要從備份組還原到新位置的每一個邏輯檔案指定 MOVE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-227">Specify a MOVE statement for every logical file you want to restore from the backup set to a new location.</span></span>  
  
    |<span data-ttu-id="1dbbb-228">選項</span><span class="sxs-lookup"><span data-stu-id="1dbbb-228">Option</span></span>|<span data-ttu-id="1dbbb-229">描述</span><span class="sxs-lookup"><span data-stu-id="1dbbb-229">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="1dbbb-230">*logical_file_name_in_backup*</span><span class="sxs-lookup"><span data-stu-id="1dbbb-230">*logical_file_name_in_backup*</span></span>|<span data-ttu-id="1dbbb-231">指定備份組中資料或記錄檔的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-231">Specifies the logical name of a data or log file in the backup set.</span></span> <span data-ttu-id="1dbbb-232">備份組中資料或記錄檔的邏輯檔案名稱，會與當初建立備份組時資料庫中的邏輯名稱相符。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-232">The logical file name of a data or log file in a backup set matches its logical name in the database when the backup set was created.</span></span><br /><br /> <span data-ttu-id="1dbbb-233">注意:若要取得備份組中的邏輯檔清單，請使用 [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-233">Note: To obtain a list of the logical files from the backup set, use [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>|  
    |<span data-ttu-id="1dbbb-234">*operating_system_file_name*</span><span class="sxs-lookup"><span data-stu-id="1dbbb-234">*operating_system_file_name*</span></span>|<span data-ttu-id="1dbbb-235">針對 *logical_file_name_in_backup*所指定的檔案指定新的位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-235">Specifies a new location for the file specified by *logical_file_name_in_backup*.</span></span> <span data-ttu-id="1dbbb-236">檔案將還原至這個位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-236">The file will be restored to this location.</span></span><br /><br /> <span data-ttu-id="1dbbb-237">(選擇性) *operating_system_file_name* 會針對還原的檔案指定新的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-237">Optionally, *operating_system_file_name* specifies a new file name for the restored file.</span></span> <span data-ttu-id="1dbbb-238">如果您要在相同的伺服器執行個體上建立現有資料庫的副本，這就是必要選項。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-238">This is necessary if you are creating a copy of an existing database on the same server instance.</span></span>|  
    |<span data-ttu-id="1dbbb-239">*n*</span><span class="sxs-lookup"><span data-stu-id="1dbbb-239">*n*</span></span>|<span data-ttu-id="1dbbb-240">這是預留位置，表示您可以指定其他 MOVE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-240">Is a placeholder indicating that you can specify additional MOVE statements.</span></span>|  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1dbbb-241">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1dbbb-241">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1dbbb-242">此範例會透過還原 `MyAdvWorks` 範例資料庫的備份 (其中包括兩個檔案： [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] _Data 和 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log)，建立名為 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]的新資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-242">This example creates a new database named `MyAdvWorks` by restoring a backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database, which includes two files: [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log.</span></span> <span data-ttu-id="1dbbb-243">這個資料庫會使用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-243">This database uses the simple recovery model.</span></span> <span data-ttu-id="1dbbb-244">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫已經存在伺服器執行個體上，因此備份中的檔案都必須還原至新的位置。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-244">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database already exists on the server instance, so the files in the backup must be restored to a new location.</span></span> <span data-ttu-id="1dbbb-245">RESTORE FILELISTONLY 陳述式是用來決定資料庫中所要還原的檔案數目及名稱。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-245">The RESTORE FILELISTONLY statement is used to determine the number and names of the files in the database being restored.</span></span> <span data-ttu-id="1dbbb-246">此資料庫備份是備份裝置上的第一個備份組。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-246">The database backup is the first backup set on the backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1dbbb-247">備份和還原交易記錄 (包括時間點還原) 的範例會使用從 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 建立的 `MyAdvWorks_FullRM` 資料庫，就如同以下 `MyAdvWorks` 範例。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-247">The examples of backing up and restoring the transaction log, including point-in-time restores, use the `MyAdvWorks_FullRM` database that is created from [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] just like the following `MyAdvWorks` example.</span></span> <span data-ttu-id="1dbbb-248">不過，您必須使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，將產生的 `MyAdvWorks_FullRM` 資料庫變更為使用完整復原模式：ALTER DATABASE <資料庫名稱> SET RECOVERY FULL。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-248">However, the resulting `MyAdvWorks_FullRM` database must be changed to use the full recovery model by using the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement: ALTER DATABASE <database_name> SET RECOVERY FULL.</span></span>  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
-- AdventureWorks2012_Backup is the name of the backup device.  
RESTORE FILELISTONLY  
   FROM AdventureWorks2012_Backup;  
-- Restore the files for MyAdvWorks.  
RESTORE DATABASE MyAdvWorks  
   FROM AdventureWorks2012_Backup  
   WITH RECOVERY,  
   MOVE 'AdventureWorks2012_Data' TO 'D:\MyData\MyAdvWorks_Data.mdf',   
   MOVE 'AdventureWorks2012_Log' TO 'F:\MyLog\MyAdvWorks_Log.ldf';  
GO  
  
```  
  
 <span data-ttu-id="1dbbb-249">如需如何建立 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫之完整資料庫備份的範例，請參閱 [建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbbb-249">For an example of how to create a full database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1dbbb-250">相關工作</span><span class="sxs-lookup"><span data-stu-id="1dbbb-250">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1dbbb-251">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1dbbb-251">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="1dbbb-252">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1dbbb-252">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="1dbbb-253">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1dbbb-253">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="1dbbb-254">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1dbbb-254">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="1dbbb-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dbbb-255">See Also</span></span>  
 <span data-ttu-id="1dbbb-256">[在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="1dbbb-256">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 <span data-ttu-id="1dbbb-257">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1dbbb-257">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="1dbbb-258">使用備份與還原複製資料庫</span><span class="sxs-lookup"><span data-stu-id="1dbbb-258">Copy Databases with Backup and Restore</span></span>](../databases/copy-databases-with-backup-and-restore.md)  
  
  
