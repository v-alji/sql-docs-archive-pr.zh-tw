---
title: 備份、還原和移動 SSIS 目錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9de552ddd54168f516f42d9988302561616fd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594663"
---
# <a name="backup-restore-and-move-the-ssis-catalog"></a><span data-ttu-id="c94e3-102">備份、 還原和移動的 SSIS 目錄</span><span class="sxs-lookup"><span data-stu-id="c94e3-102">Backup, Restore, and Move the SSIS Catalog</span></span>
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] <span data-ttu-id="c94e3-103">包括 SSISDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c94e3-103">includes the SSISDB database.</span></span> <span data-ttu-id="c94e3-104">您可以查詢 SSISDB 資料庫中的檢視，以檢查物件、設定以及儲存在 [SSISDB] 目錄中的作業資料。</span><span class="sxs-lookup"><span data-stu-id="c94e3-104">You query views in the SSISDB database to inspect objects, settings, and operational data that are stored in the **SSISDB** catalog.</span></span> <span data-ttu-id="c94e3-105">本主題提供備份與還原資料庫的指示。</span><span class="sxs-lookup"><span data-stu-id="c94e3-105">This topic provides instructions for backing up and restoring the database.</span></span>  
  
 <span data-ttu-id="c94e3-106">**SSISDB** 目錄會儲存您已經部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器的封裝。</span><span class="sxs-lookup"><span data-stu-id="c94e3-106">The **SSISDB** catalog stores the packages that you've deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="c94e3-107">如需目錄的詳細資訊，請參閱 [SSIS 目錄](catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-107">For more information about the catalog, see [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
##  <a name="to-back-up-the-ssis-database"></a><a name="backup"></a> <span data-ttu-id="c94e3-108">若要備份 SSIS 資料庫</span><span class="sxs-lookup"><span data-stu-id="c94e3-108">To Back up the SSIS Database</span></span>  
  
1.  <span data-ttu-id="c94e3-109">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 並連接至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c94e3-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="c94e3-110">使用 BACKUP MASTER KEY Transact-SQL 陳述式，備份 SSISDB 資料庫的主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="c94e3-110">Back up the master key for the SSISDB database, by using the BACKUP MASTER KEY Transact-SQL statement.</span></span> <span data-ttu-id="c94e3-111">此金鑰儲存在您指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="c94e3-111">The key is stored in a file that you specify.</span></span> <span data-ttu-id="c94e3-112">使用密碼來加密檔案中的主要金鑰密碼。</span><span class="sxs-lookup"><span data-stu-id="c94e3-112">Use a password to encrypt the master key in the file.</span></span>  
  
     <span data-ttu-id="c94e3-113">如需陳述式的詳細資訊，請參閱 [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-113">For more information about the statement, see [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
     <span data-ttu-id="c94e3-114">在下列範例中，主要金鑰是匯出至 `c:\temp directory\RCTestInstKey` 檔案。</span><span class="sxs-lookup"><span data-stu-id="c94e3-114">In the following example, the master key is exported to the `c:\temp directory\RCTestInstKey` file.</span></span> <span data-ttu-id="c94e3-115">`LS2Setup!` 密碼是用來加密主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="c94e3-115">The `LS2Setup!` password is used to encrypt the master key.</span></span>  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  <span data-ttu-id="c94e3-116">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [備份資料庫] 對話方塊備份 SSISDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c94e3-116">Back up the SSISDB database by using the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c94e3-117">如需詳細資訊，請參閱[如何：備份資料庫 (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-117">For more information, see [How to: Back Up a Database (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812).</span></span>  
  
4.  <span data-ttu-id="c94e3-118">執行下列操作，產生 ##MS_SSISServerCleanupJobLogin## 的 CREATE LOGIN 指令碼。</span><span class="sxs-lookup"><span data-stu-id="c94e3-118">Generate the CREATE LOGIN script for ##MS_SSISServerCleanupJobLogin##, by doing the following.</span></span> <span data-ttu-id="c94e3-119">如需詳細資訊，請參閱 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-119">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
    1.  <span data-ttu-id="c94e3-120">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的物件總管中，展開 [安全性] 節點，然後展開 [登入] 節點。</span><span class="sxs-lookup"><span data-stu-id="c94e3-120">In Object Explorer in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Security** node and then expand the **Logins** node.</span></span>  
  
    2.  <span data-ttu-id="c94e3-121">以滑鼠右鍵按一下 [##MS_SSISServerCleanupJobLogin##]，然後按一下 [編寫登入的指令碼為] > [CREATE 至] > [新增查詢編輯器視窗]。</span><span class="sxs-lookup"><span data-stu-id="c94e3-121">Right-click **##MS_SSISServerCleanupJobLogin##**, and then click **Script Login as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
5.  <span data-ttu-id="c94e3-122">如果您要將 SSISDB 資料庫還原至從未建立過 SSISDB 目錄的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，請執行下列動作，藉以產生 sp_ssis_startup 的 CREATE PROCEDURE 指令碼。</span><span class="sxs-lookup"><span data-stu-id="c94e3-122">If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, generate the CREATE PROCEDURE script for sp_ssis_startup, by doing the following.</span></span> <span data-ttu-id="c94e3-123">如需詳細資訊，請參閱 [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-123">For more information, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
    1.  <span data-ttu-id="c94e3-124">在物件總管中，展開 [**資料庫**] 節點，然後展開 [**系統資料庫**] [主要程式設計] [  >  **master**  >  **Programmability**  >  **預存程式**] 節點。</span><span class="sxs-lookup"><span data-stu-id="c94e3-124">In Object Explorer, expand the **Databases** node and then expand the **System Databases** > **master** > **Programmability** > **Stored Procedures** node.</span></span>  
  
    2.  <span data-ttu-id="c94e3-125">以滑鼠右鍵按一下 [dbo.sp_ssis_startup]\*\*\*\*，然後按一下 [編寫預存程序的指令碼為]\*\*\*\* > [CREATE 至]\*\*\*\* > [新增查詢編輯器視窗]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c94e3-125">Right click **dbo.sp_ssis_startup**, and then click **Script Stored Procedure as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
6.  <span data-ttu-id="c94e3-126">確認已啟動 SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="c94e3-126">Confirm that SQL Server Agent has been started</span></span>  
  
7.  <span data-ttu-id="c94e3-127">如果您要將 SSISDB 資料庫還原至從未建立過 SSISDB 目錄的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，請執行下列動作，藉以產生 SSIS 伺服器維護作業的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c94e3-127">If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, generate a script for the SSIS Server Maintenance Job by doing the following.</span></span> <span data-ttu-id="c94e3-128">當您建立 SSISDB 目錄時，系統就會自動在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 中建立指令碼。</span><span class="sxs-lookup"><span data-stu-id="c94e3-128">The script is created in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent automatically when the SSISDB catalog is created.</span></span> <span data-ttu-id="c94e3-129">此作業有助於清除保留週期外部的清除作業，並移除舊版專案。</span><span class="sxs-lookup"><span data-stu-id="c94e3-129">The job helps clean up cleanup operation logs outside the retention window and remove older versions of projects.</span></span>  
  
    1.  <span data-ttu-id="c94e3-130">在物件總管中，展開 [SQL Server Agent] 節點，然後展開 [作業] 節點。</span><span class="sxs-lookup"><span data-stu-id="c94e3-130">In Object Explorer, expand the **SQL Server Agent** node and then expand the **Jobs** node.</span></span>  
  
    2.  <span data-ttu-id="c94e3-131">以滑鼠右鍵按一下 [SSIS 伺服器維護作業]，然後按一下 [**腳本作業] 做為**[  >  **建立至**  >  **新查詢編輯器視窗]**。</span><span class="sxs-lookup"><span data-stu-id="c94e3-131">Right click SSIS Server Maintenance Job, and then click **Script Job as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
### <a name="to-restore-the-ssis-database"></a><span data-ttu-id="c94e3-132">若要還原 SSIS 資料庫</span><span class="sxs-lookup"><span data-stu-id="c94e3-132">To Restore the SSIS Database</span></span>  
  
1.  <span data-ttu-id="c94e3-133">如果您要將 SSISDB 資料庫還原至從未建立過 SSISDB 目錄的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，請執行 sp_configure 預存程序，藉以啟用 Common Language Runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-133">If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, enable common language runtime (clr) by running the sp_configure stored procedure.</span></span> <span data-ttu-id="c94e3-134">如需詳細資訊，請參閱 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 和 [CLR 已啟用選項](https://go.microsoft.com/fwlink/?LinkId=231855)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-134">For more information, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) and [clr enabled Option](https://go.microsoft.com/fwlink/?LinkId=231855).</span></span>  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  <span data-ttu-id="c94e3-135">如果您要將 SSISDB 資料庫還原至從未建立過 SSISDB 目錄的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，請建立非對稱金鑰並根據非對稱金鑰建立登入，並且將 UNSAFE 權限授與登入。</span><span class="sxs-lookup"><span data-stu-id="c94e3-135">If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, create the asymmetric key and the login from the asymmetric key, and grant UNSAFE permission to the login.</span></span>  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="c94e3-136">CLR 預存程序需要授與 UNSAFE 權限給登入，因為登入需要對於限制資源的額外存取，例如 Microsoft Win32 API。</span><span class="sxs-lookup"><span data-stu-id="c94e3-136">CLR stored procedures require UNSAFE permissions to be granted to the login because the login requires additional access to restricted resources, such as the Microsoft Win32 API.</span></span> <span data-ttu-id="c94e3-137">如需 UNSAFE 程式碼權限的詳細資訊，請參閱 [建立組件](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-137">For more information about the UNSAFE code permission, see [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).</span></span>  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  <span data-ttu-id="c94e3-138">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [還原資料庫] 對話方塊，從備份還原 SSISDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c94e3-138">Restore the SSISDB database from the backup by using the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c94e3-139">如需詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="c94e3-139">For more information, see the following topics.</span></span>  
  
    -   [<span data-ttu-id="c94e3-140">還原資料庫 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c94e3-140">Restore Database &#40;General Page&#41;</span></span>](general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="c94e3-141">還原資料庫 &#40;檔案頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c94e3-141">Restore Database &#40;Files Page&#41;</span></span>](../relational-databases/backup-restore/restore-database-files-page.md)  
  
    -   [<span data-ttu-id="c94e3-142">還原資料庫 &#40;選項頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c94e3-142">Restore Database &#40;Options Page&#41;</span></span>](../relational-databases/backup-restore/restore-database-options-page.md)  
  
4.  <span data-ttu-id="c94e3-143">針對 ##MS_SSISServerCleanupJobLogin##、sp_ssis_startup 和 SSIS 伺服器維護作業，執行您在 [備份 SSIS 資料庫](#backup) 中所建立的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c94e3-143">Execute the scripts that you created in the [To Back up the SSIS Database](#backup) for ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup, and SSIS Server Maintenance Job.</span></span> <span data-ttu-id="c94e3-144">確認已啟動 SQL Server Agent。</span><span class="sxs-lookup"><span data-stu-id="c94e3-144">Confirm that SQL Server Agent has been started.</span></span>  
  
5.  <span data-ttu-id="c94e3-145">執行下列陳述式以設定 sp_ssis_startup 程序進行自動執行。</span><span class="sxs-lookup"><span data-stu-id="c94e3-145">Run the following statement to set the sp_ssis_startup prodecure for autoexecution.</span></span> <span data-ttu-id="c94e3-146">如需詳細資訊，請參閱 [sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-146">For more information, see [sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql).</span></span>  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  <span data-ttu-id="c94e3-147">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [登入屬性] 對話方塊，將 SSISDB 使用者 ##MS_SSISServerCleanupJobUser## (SSISDB 資料庫) 對應至 ##MS_SSISServerCleanupJobLogin##。</span><span class="sxs-lookup"><span data-stu-id="c94e3-147">Map the SSISDB user ##MS_SSISServerCleanupJobUser## (SSISDB database) to ##MS_SSISServerCleanupJobLogin##, by using the **Login Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
7.  <span data-ttu-id="c94e3-148">使用下列其中一種方法來還原主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="c94e3-148">Restore the master key by using one of the following methods.</span></span> <span data-ttu-id="c94e3-149">如需加密的詳細資訊，請參閱 [加密階層](../relational-databases/security/encryption/encryption-hierarchy.md)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-149">For more information about encryption, see [Encryption Hierarchy](../relational-databases/security/encryption/encryption-hierarchy.md).</span></span>  
  
    -   <span data-ttu-id="c94e3-150">**方法 1**</span><span class="sxs-lookup"><span data-stu-id="c94e3-150">**Method 1**</span></span>  
  
         <span data-ttu-id="c94e3-151">如果您已經備份資料庫主要金鑰，而且您有用來加密主要金鑰的密碼，請使用此方法。</span><span class="sxs-lookup"><span data-stu-id="c94e3-151">Use this method if you've already performed a backup of the database master key, and you have the password used to encrypt the master key.</span></span>  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="c94e3-152">確認 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服務帳戶擁有讀取備份金鑰檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="c94e3-152">Confirm that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service account has permissions to read the backup key file.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c94e3-153">如果服務主要金鑰尚未加密資料庫主要金鑰，您將會看到下列警告訊息顯示在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="c94e3-153">You will see the following warning message displayed in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] if the database master key has not yet been encrypted by the service master key.</span></span> <span data-ttu-id="c94e3-154">忽略警告訊息。</span><span class="sxs-lookup"><span data-stu-id="c94e3-154">Ignore the warning message.</span></span>  
        >   
        >  <span data-ttu-id="c94e3-155">**無法解密目前的主要金鑰。因為指定了 FORCE 選項，因此忽略了這個錯誤。**</span><span class="sxs-lookup"><span data-stu-id="c94e3-155">**The current master key cannot be decrypted. The error was ignored because the FORCE option was specified.**</span></span>  
        >   
        >  <span data-ttu-id="c94e3-156">FORCE 引數會指定即使未開放目前的資料庫主要金鑰，也應該繼續還原程序。</span><span class="sxs-lookup"><span data-stu-id="c94e3-156">The FORCE argument specifies that the restore process should continue even if the current database master key is not open.</span></span> <span data-ttu-id="c94e3-157">若是 SSISDB 目錄，因為尚未在您要還原資料庫所在的執行個體上開放資料庫主要金鑰，因此您將會看到此訊息。</span><span class="sxs-lookup"><span data-stu-id="c94e3-157">For the SSISDB catalog, because the database master key has not been opened on the instance where you are restoring the database, you will see this message.</span></span>  
  
    -   <span data-ttu-id="c94e3-158">**方法 2**</span><span class="sxs-lookup"><span data-stu-id="c94e3-158">**Method 2**</span></span>  
  
         <span data-ttu-id="c94e3-159">如果您有建立 SSISDB 所使用的原始密碼，請使用此方法。</span><span class="sxs-lookup"><span data-stu-id="c94e3-159">Use this method if you have the original password that was used to create SSISDB.</span></span>  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  <span data-ttu-id="c94e3-160">執行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.check_schema_version [，以判斷 SSISDB 目錄結構描述與](/sql/integration-services/system-stored-procedures/catalog-check-schema-version)二進位檔 (ISServerExec 和 SQLCLR 組件) 是否相容。</span><span class="sxs-lookup"><span data-stu-id="c94e3-160">Determine whether the SSISDB catalog schema and the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] binaries (ISServerExec and SQLCLR assembly) are compatible, by running [catalog.check_schema_version](/sql/integration-services/system-stored-procedures/catalog-check-schema-version).</span></span>  
  
9. <span data-ttu-id="c94e3-161">若要確認已成功還原 SSISDB 資料庫，請針對 SSISDB 目錄執行作業，例如執行已經部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器的封裝。</span><span class="sxs-lookup"><span data-stu-id="c94e3-161">To confirm that the SSISDB database has been restored successfully, perform operations against the SSISDB catalog such as running packages that have been deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="c94e3-162">如需詳細資訊，請參閱 [使用 SQL Server Management Studio 在 SSIS 伺服器上執行封裝](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-162">For more information, see [Run a Package on the SSIS Server Using SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md).</span></span>  
  
### <a name="to-move-the-ssis-database"></a><span data-ttu-id="c94e3-163">若要移動 SSIS 資料庫</span><span class="sxs-lookup"><span data-stu-id="c94e3-163">To Move the SSIS Database</span></span>  
  
-   <span data-ttu-id="c94e3-164">遵循移動使用者資料庫的指示進行。</span><span class="sxs-lookup"><span data-stu-id="c94e3-164">Follow the instructions for moving user databases.</span></span> <span data-ttu-id="c94e3-165">如需詳細資訊，請參閱 [移動使用者資料庫](../relational-databases/databases/move-user-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-165">For more information, see [Move User Databases](../relational-databases/databases/move-user-databases.md).</span></span>  
  
     <span data-ttu-id="c94e3-166">確定您有備份 SSISDB 資料庫的主要金鑰並保護備份檔案。</span><span class="sxs-lookup"><span data-stu-id="c94e3-166">Ensure that you back up the master key for the SSISDB database and protect the backup file.</span></span> <span data-ttu-id="c94e3-167">如需詳細資訊，請參閱 [備份 SSIS 資料庫](#backup)。</span><span class="sxs-lookup"><span data-stu-id="c94e3-167">For more information, see [To Back up the SSIS Database](#backup).</span></span>  
  
     <span data-ttu-id="c94e3-168">確定 Integration Services (SSIS) 相關物件建立在尚未建立 SSISDB 目錄的新 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="c94e3-168">Ensure that the Integration Services (SSIS) relevant objects are created in the new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog has not yet been created.</span></span>  
  
  
