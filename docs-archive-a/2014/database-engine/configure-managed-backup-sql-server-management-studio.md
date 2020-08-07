---
title: 設定受管理的備份 (SQL Server Management Studio) |Microsoft Docs
description: 使用 [受管理的備份] 對話方塊，將 SQL Server 受管理的備份設定為 Azure 預設值。 瞭解您需要考慮的選項。
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e952ef1102ac67bd0ed9f72d0c201d54b320b5ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584736"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a><span data-ttu-id="72c05-104">設定受管理的備份 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="72c05-104">Configure Managed Backup (SQL Server Management Studio)</span></span>
  <span data-ttu-id="72c05-105">**[受管理的備份]** 對話方塊可讓您設定執行個體的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 預設值。</span><span class="sxs-lookup"><span data-stu-id="72c05-105">The **Managed Backup** dialog allows you to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] defaults for the instance.</span></span> <span data-ttu-id="72c05-106">本主題說明如何使用此對話方塊來設定執行個體的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 預設設定，和您在這麼做時必須考量的選項。</span><span class="sxs-lookup"><span data-stu-id="72c05-106">This topic describes how to use this dialog to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] default settings for the instance and options you must consider when doing so.</span></span> <span data-ttu-id="72c05-107">在設定執行個體的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 時，設定會套用至之後建立的任何新資料庫。</span><span class="sxs-lookup"><span data-stu-id="72c05-107">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured for the instance, the settings are applied to any new database created thereafter.</span></span>  
  
 <span data-ttu-id="72c05-108">如果您想要 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 針對特定資料庫進行設定，請參閱[針對資料庫啟用和設定 SQL Server 受控備份至 Azure](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)。</span><span class="sxs-lookup"><span data-stu-id="72c05-108">If you want to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database, see [Enable and Configure SQL Server Managed Backup to Azure for a Database](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="72c05-109">SQL Server Managed Backup 不支援 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="72c05-109">SQL Server Managed Backup is not supported with proxy servers.</span></span> 
  
## <a name="task-list"></a><span data-ttu-id="72c05-110">工作清單</span><span class="sxs-lookup"><span data-stu-id="72c05-110">Task List</span></span>  
  
## <a name="ss_smartbackup-functions-using-managed-backup-interface-in-sql-server-management-studio"></a><span data-ttu-id="72c05-111">在 SQL Server Management Studio 中使用 Backup Interface 介面的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 函數</span><span class="sxs-lookup"><span data-stu-id="72c05-111">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Functions Using Managed Backup Interface in SQL Server Management Studio</span></span>  
 <span data-ttu-id="72c05-112">在此版本中，您只可以使用 **[管理備份]** 介面設定的執行個體層級的預設設定。</span><span class="sxs-lookup"><span data-stu-id="72c05-112">In this release, you can only configure instance level default settings using the **Management Backup** interface.</span></span> <span data-ttu-id="72c05-113">您無法設定資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 、暫停或繼續 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 作業，或設定電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="72c05-113">You cannot configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database, pause or resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operations, or setup email notifications.</span></span> <span data-ttu-id="72c05-114">如需如何透過**受管理的備份**介面執行目前不支援之作業的相關資訊，請參閱[SQL Server 受控備份至 Azure-保留和儲存體設定](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="72c05-114">For information on how to perform operations not currently supported through the **Managed Backup** interface, see [SQL Server Managed Backup to Azure - Retention and Storage Settings](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="72c05-115">權限</span><span class="sxs-lookup"><span data-stu-id="72c05-115">Permissions</span></span>  
 <span data-ttu-id="72c05-116">**在 SQL Server Management Studio 中檢視 Managed Backup 節點：** 若要在  **[物件總管]** 中檢視 **Managed Backup**節點，您必須是系統管理員，或具有下列為您的使用者帳戶特別授與的權限：</span><span class="sxs-lookup"><span data-stu-id="72c05-116">**View Managed Backup Node is SQL Server Management Studio:** To view  **Managed Backup** node in **Object Explorer**, you must either be a System Admin or have the following permissions specifically granted to your user account:</span></span>  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   <span data-ttu-id="72c05-117">`EXECUTE` 上的 `smart_admin.fn_is_master_switch_on`。</span><span class="sxs-lookup"><span data-stu-id="72c05-117">`EXECUTE` on `smart_admin.fn_is_master_switch_on`.</span></span>  
  
-   <span data-ttu-id="72c05-118">`SELECT` 上的 `smart_admin.fn_backup_instance_config`。</span><span class="sxs-lookup"><span data-stu-id="72c05-118">`SELECT` on `smart_admin.fn_backup_instance_config`.</span></span>  
  
 <span data-ttu-id="72c05-119">**若要設定 Managed Backup：** 若要在 SQL Server Management Studio 中設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，您必須是系統管理員，或具有下列權限：</span><span class="sxs-lookup"><span data-stu-id="72c05-119">**To Configure Managed Backup:** to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] in SQL Server Management Studio, you must be a System Administrator or have the following permissions:</span></span>  
  
 <span data-ttu-id="72c05-120">`db_backupoperator` 資料庫角色的成員資格，且該角色必須具有 `ALTER ANY CREDENTIAL` 權限，以及 `sp_delete_backuphistory` 預存程序的 `EXECUTE` 權限。</span><span class="sxs-lookup"><span data-stu-id="72c05-120">Membership in `db_backupoperator` database role, with `ALTER ANY CREDENTIAL` permissions, and `EXECUTE` permissions on `sp_delete_backuphistory` stored procedure.</span></span>  
  
 <span data-ttu-id="72c05-121">`smart_admin.fn_get_current_xevent_settings` 函數的 `SELECT` 權限。</span><span class="sxs-lookup"><span data-stu-id="72c05-121">`SELECT` permissions on the `smart_admin.fn_get_current_xevent_settings` function.</span></span>  
  
 <span data-ttu-id="72c05-122">`EXECUTE`預存程式的許可權 `smart_admin.sp_get_backup_diagnostics` 。</span><span class="sxs-lookup"><span data-stu-id="72c05-122">`EXECUTE` permissions on the `smart_admin.sp_get_backup_diagnostics` stored procedure.</span></span> <span data-ttu-id="72c05-123">除此之外，因為它會從內部呼叫其他需要此權限的系統物件，所以還需要 `VIEW SERVER STATE` 權限。</span><span class="sxs-lookup"><span data-stu-id="72c05-123">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
 <span data-ttu-id="72c05-124">`smart_admin.sp_set_instance_backup` 的 `EXECUTE` 權限和 `smart_admin.sp_backup_master_switch`。</span><span class="sxs-lookup"><span data-stu-id="72c05-124">`EXECUTE` permissions on `smart_admin.sp_set_instance_backup`, and `smart_admin.sp_backup_master_switch`.</span></span>  
  
## <a name="configure-ss_smartbackup-using-sql-server-management-studio"></a><span data-ttu-id="72c05-125">使用 SQL Server Management Studio 設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72c05-125">Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] using SQL Server Management Studio</span></span>  
 <span data-ttu-id="72c05-126">從 **[物件總管]** 展開 **[管理]** 節點，並以滑鼠右鍵按一下 **[Managed Backup]**。</span><span class="sxs-lookup"><span data-stu-id="72c05-126">From the **object explorer**, expand the **Management** node, and right click on **Managed Backup**.</span></span> <span data-ttu-id="72c05-127">選取 [設定] 。</span><span class="sxs-lookup"><span data-stu-id="72c05-127">Select **Configure**.</span></span> <span data-ttu-id="72c05-128">這樣會開啟 **[Managed Backup]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="72c05-128">This opens the **Managed Backup** dialog.</span></span>  
  
 <span data-ttu-id="72c05-129">勾選 **[啟用 Managed Backup]** 選項，並指定組態值：</span><span class="sxs-lookup"><span data-stu-id="72c05-129">Check **Enable Managed Backup** option and specify the configuration values:</span></span>  
  
 <span data-ttu-id="72c05-130">**[檔案保留]** 期間以天為單位指定，且應介於 1 到 30 之間。</span><span class="sxs-lookup"><span data-stu-id="72c05-130">The **File retention** period is specified in days and should be between 1 and 30.</span></span>  
  
 <span data-ttu-id="72c05-131">您選取的 **[SQL 認證]** 應符合儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="72c05-131">The **SQL Credential** you select should match the storage account.</span></span> <span data-ttu-id="72c05-132">如果您目前沒有儲存驗證資訊的 SQL 認證，您可以按一下 **[建立]** 加以建立。</span><span class="sxs-lookup"><span data-stu-id="72c05-132">If you currently do not have a SQL Credential that stores the authentication information, you can create one by clicking **Create**.</span></span> <span data-ttu-id="72c05-133">您也可以使用 CREATE CREDENTIAL Transact-SQL 陳述式來建立認證，並提供識別的儲存體帳戶名稱和 SECRET 參數的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="72c05-133">You can also create credential by using the CREATE CREDENTIAL Transact-SQL statement, and provide the storage account name for Identity and the access key for the SECRET parameters.</span></span> <span data-ttu-id="72c05-134">如需詳細資訊，請參閱＜ [Create a Credential](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential)＞。</span><span class="sxs-lookup"><span data-stu-id="72c05-134">For more information, see [Create a Credential](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).</span></span>  
  
 <span data-ttu-id="72c05-135">指定 Azure 儲存體帳戶的**儲存體 URL** 、儲存儲存體帳戶之驗證資訊的 SQL 認證，以及備份檔案的保留期限。</span><span class="sxs-lookup"><span data-stu-id="72c05-135">Specify the **Storage URL** for the Azure storage account, the SQL Credential that stores the authentication information for the storage account, and the retention period for the backup files.</span></span>  
  
 <span data-ttu-id="72c05-136">儲存體 URL 格式為： HTTPs:// \<StorageAccount> . blob.core.windows.net/</span><span class="sxs-lookup"><span data-stu-id="72c05-136">The storage URL format is: https://\<StorageAccount>.blob.core.windows.net/</span></span>  
  
 <span data-ttu-id="72c05-137">若要設定執行個體層級的加密設定，請勾選 **[加密備份]** 選項，並指定演算法，和用於加密的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="72c05-137">To set the encryption settings at the instance level, check **Encrypt Backup** option, and specify the algorithm and a Certificate or Asymmetric Key to use for the encryption.</span></span>  <span data-ttu-id="72c05-138">這會在執行個體層級進行設定，並且在套用此組態之後用於所有建立的新資料庫。</span><span class="sxs-lookup"><span data-stu-id="72c05-138">This is set at the instance level is used for all the new databases created once this configuration has been applied.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="72c05-139">若未設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，則此對話方塊無法用來指定加密選項。</span><span class="sxs-lookup"><span data-stu-id="72c05-139">This dialog cannot be used to specify the encryption options without configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="72c05-140">這些加密選項僅適用於 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 作業。</span><span class="sxs-lookup"><span data-stu-id="72c05-140">These encryption options only apply to [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operations.</span></span> <span data-ttu-id="72c05-141">若要在其他備份程序中使用加密，請參閱 [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="72c05-141">To use encryption for other backup procedures, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
### <a name="considerations"></a><span data-ttu-id="72c05-142">考量</span><span class="sxs-lookup"><span data-stu-id="72c05-142">Considerations</span></span>  
 <span data-ttu-id="72c05-143">如果您在執行個體層級設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，設定會套用至之後建立的任何新資料庫。</span><span class="sxs-lookup"><span data-stu-id="72c05-143">If you configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the instance level, the settings are applied to any new database created thereafter.</span></span>  <span data-ttu-id="72c05-144">不過，現有的資料庫將不會自動繼承這些設定。</span><span class="sxs-lookup"><span data-stu-id="72c05-144">However, existing database will not automatically inherit these settings.</span></span> <span data-ttu-id="72c05-145">若要在先前已存在的資料庫上設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，您必須個別設定每個資料庫。</span><span class="sxs-lookup"><span data-stu-id="72c05-145">To configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on previously existing databases, you must configure each database specifically.</span></span> <span data-ttu-id="72c05-146">如需詳細資訊，請參閱[針對資料庫啟用和設定 SQL Server 受控備份至 Azure](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)。</span><span class="sxs-lookup"><span data-stu-id="72c05-146">For more information, see [Enable and Configure SQL Server Managed Backup to Azure for a Database](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).</span></span>  
  
 <span data-ttu-id="72c05-147">如果 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 已使用暫停 `smart_admin.sp_backup_master_switch` ，您會看到一則警告訊息「Managed Backup 已停用，而目前的設定將不會生效 ...」當您嘗試完成設定時。</span><span class="sxs-lookup"><span data-stu-id="72c05-147">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has been paused using the `smart_admin.sp_backup_master_switch`, you will see a warning message " Managed Backup is disabled and the current configurations will not take effect..." when you try to complete the configuration.</span></span> <span data-ttu-id="72c05-148">使用 `smart_admin.sp_backup_master_switch` 預存並設定 @new_state = 1。</span><span class="sxs-lookup"><span data-stu-id="72c05-148">Use the `smart_admin.sp_backup_master_switch` stored and set the @new_state=1.</span></span> <span data-ttu-id="72c05-149">這將會繼續 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服務，且組態設定將會生效。</span><span class="sxs-lookup"><span data-stu-id="72c05-149">This will resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services and the configuration settings will take into effect.</span></span> <span data-ttu-id="72c05-150">如需預存程式的詳細資訊，請參閱[smart_admin. sp_ backup_master_switch &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="72c05-150">For more information on the stored procedure, see [smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c05-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72c05-151">See Also</span></span>  
 [<span data-ttu-id="72c05-152">SQL Server Managed Backup 到 Azure：互通性與共存性</span><span class="sxs-lookup"><span data-stu-id="72c05-152">SQL Server Managed Backup to Azure: Interoperability and Coexistence</span></span>](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
