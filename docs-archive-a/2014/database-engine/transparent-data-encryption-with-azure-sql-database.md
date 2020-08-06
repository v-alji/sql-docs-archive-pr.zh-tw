---
title: Azure SQL Database 的透明資料加密 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6af7c52741b85a2733b93c2b1ed8c03a14dd6343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596242"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a><span data-ttu-id="c59b9-102">Azure SQL Database 的透明資料加密</span><span class="sxs-lookup"><span data-stu-id="c59b9-102">Transparent Data Encryption with Azure SQL Database</span></span>
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] <span data-ttu-id="c59b9-103">透明資料加密 (預覽版) 可即時執行資料庫、相關聯備份及交易檔的即時加密與解密，完全無須變更應用程式，就能協助防範惡意活動所帶來的威脅。</span><span class="sxs-lookup"><span data-stu-id="c59b9-103">transparent data encryption (preview) helps protect against the threat of malicious activity by performing real-time encryption and decryption of the database, associated backups, and transaction log files at rest without requiring changes to the application.</span></span>

 <span data-ttu-id="c59b9-104">TDE 會使用稱為資料庫加密金鑰的對稱金鑰來加密整個資料庫的儲存體。</span><span class="sxs-lookup"><span data-stu-id="c59b9-104">TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key.</span></span> <span data-ttu-id="c59b9-105">在 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 中，資料庫加密金鑰由內建的伺服器憑證保護。</span><span class="sxs-lookup"><span data-stu-id="c59b9-105">In [!INCLUDE[ssSDS](../includes/sssds-md.md)] the database encryption key is protected by a built-in server certificate.</span></span> <span data-ttu-id="c59b9-106">每部 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 伺服器各有其專用的內建伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="c59b9-106">The built-in server certificate is unique for each [!INCLUDE[ssSDS](../includes/sssds-md.md)] server.</span></span> <span data-ttu-id="c59b9-107">若資料庫具有 GeoDR 關聯性，則由每部伺服器上不同的金鑰保護。</span><span class="sxs-lookup"><span data-stu-id="c59b9-107">If a database is in a GeoDR relationship, it is protected by a different key on each server.</span></span> <span data-ttu-id="c59b9-108">如有 2 個資料庫同時連線到同一部伺服器，則這兩個資料庫會共用同一個內建憑證。</span><span class="sxs-lookup"><span data-stu-id="c59b9-108">If 2 databases are connected to the same server, they share the same built-in certificate.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="c59b9-109">會每隔 90 天自動輪換這些憑證。</span><span class="sxs-lookup"><span data-stu-id="c59b9-109">automatically rotates these certificates at least every 90 days.</span></span> <span data-ttu-id="c59b9-110">如需 TDE 的一般說明，請參閱 [透明資料加密 &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="c59b9-110">For a general description of TDE, see [Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md).</span></span>

 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] <span data-ttu-id="c59b9-111">不支援 Azure 金鑰保存庫與 TDE 整合。</span><span class="sxs-lookup"><span data-stu-id="c59b9-111">does not support Azure Key Vault integration with TDE.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="c59b9-112">可以使用金鑰保存庫中的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="c59b9-112">running on an Azure virtual machine can use an asymmetric key from the Key Vault.</span></span> <span data-ttu-id="c59b9-113">如需詳細資訊，請參閱＜ [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA)＞。</span><span class="sxs-lookup"><span data-stu-id="c59b9-113">For more information, see [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA).</span></span>

||
|-|
|<span data-ttu-id="c59b9-114">**適用**于： [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] [某些區域中的 (預覽](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) 。</span><span class="sxs-lookup"><span data-stu-id="c59b9-114">**Applies to**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([Preview in some regions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="c59b9-115">目前是預覽功能。</span><span class="sxs-lookup"><span data-stu-id="c59b9-115">This is currently a preview feature.</span></span> <span data-ttu-id="c59b9-116">我了解並同意在我的資料庫中實作 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 透明資料加密必須遵守授權合約之預覽條款 (例如 Enterprise 合約、Microsoft Azure 合約或 Microsoft 線上訂用帳戶合約) 及任何適行 [Microsoft Azure Preview 增補使用條款](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)的規定。</span><span class="sxs-lookup"><span data-stu-id="c59b9-116">I acknowledge and agree that implementation of [!INCLUDE[ssSDS](../includes/sssds-md.md)] transparent data encryption in my database(s) is subject to the preview terms in my license agreement (e.g. the Enterprise Agreement, Microsoft Azure Agreement, or Microsoft Online Subscription Agreement), as well as any applicable [Supplemental Terms of Use for Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).</span></span>

 <span data-ttu-id="c59b9-117">TDE 狀態預覽即使在 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 版本系列 V12 已宣佈為目前處於公開可用狀態的地理區域也適用。</span><span class="sxs-lookup"><span data-stu-id="c59b9-117">The preview of status of TDE applies even in the subset of geographic regions where version family V12 of [!INCLUDE[ssSDS](../includes/sssds-md.md)] is announced as now being in general availability status.</span></span> <span data-ttu-id="c59b9-118">在 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 宣佈 TDE 從預覽版升級至 GA 前， [!INCLUDE[msCoName](../includes/msconame-md.md)] 的 TDE 並不適用於生產資料庫。</span><span class="sxs-lookup"><span data-stu-id="c59b9-118">TDE for [!INCLUDE[ssSDS](../includes/sssds-md.md)] is not intended for use in production databases until [!INCLUDE[msCoName](../includes/msconame-md.md)] announces that TDE is promoted from preview to GA.</span></span> <span data-ttu-id="c59b9-119">如需有關 [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12 的詳細資訊，請參閱 [Azure SQL Database 的新功能](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)。</span><span class="sxs-lookup"><span data-stu-id="c59b9-119">For more information about [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12, see [What's new in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).</span></span>

##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c59b9-120">權限</span><span class="sxs-lookup"><span data-stu-id="c59b9-120">Permissions</span></span>
 <span data-ttu-id="c59b9-121">若要註冊預覽版，並透過 Azure 入口網站利用 REST API 或 PowerShell 設定 TDE，您必須以 Azure 擁有者、參與者或 SQL 安全性管理員的身分連線。</span><span class="sxs-lookup"><span data-stu-id="c59b9-121">To sign up for the preview and to configure TDE through the Azure portal, by using the REST API, or by using PowerShell, you must be connected as the Azure Owner, Contributor, or SQL Security Manager.</span></span>

 <span data-ttu-id="c59b9-122">若要設定使用 [!INCLUDE[tsql](../includes/tsql-md.md)] 設定 TDE，必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="c59b9-122">To configure TDE by using [!INCLUDE[tsql](../includes/tsql-md.md)] requires the following:</span></span>

-   <span data-ttu-id="c59b9-123">您必須已經註冊 TDE 預覽版。</span><span class="sxs-lookup"><span data-stu-id="c59b9-123">You must be already signed up for the TDE preview.</span></span>

-   <span data-ttu-id="c59b9-124">若要建立資料庫的加密金鑰，您必須是 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 系統管理員，或是 master 資料庫中之 **dbmanager** 角色的成員，並具備該資料庫的 **CONTROL** 權限。</span><span class="sxs-lookup"><span data-stu-id="c59b9-124">To create the database encryption key you must be a [!INCLUDE[ssSDS](../includes/sssds-md.md)] administrator or you must be a member of the **dbmanager** role in the master database and have the **CONTROL** permission on the database.</span></span>

-   <span data-ttu-id="c59b9-125">若要執行 ALTER DATABASE 陳述式與 SET 選項，便只需要具備 **dbmanager** 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="c59b9-125">To execute the ALTER DATABASE statement with the SET option only requires membership in the **dbmanager** role.</span></span>

##  <a name="sign-up-for-the-preview-of-tde-and-enable-tde-on-a-database"></a><a name="Preview"></a><span data-ttu-id="c59b9-126">註冊 TDE 的預覽，並在資料庫上啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="c59b9-126">Sign Up for the Preview of TDE and Enable TDE on a Database</span></span>

1.  <span data-ttu-id="c59b9-127">請造訪 Azure 入口網站 [https://portal.azure.com](https://portal.azure.com) ，並使用您的 Azure 系統管理員或參與者帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c59b9-127">Visit the Azure Portal at [https://portal.azure.com](https://portal.azure.com) and sign-in with your Azure Administrator or Contributor account.</span></span>

2.  <span data-ttu-id="c59b9-128">在左邊的橫幅中，按一下以**瀏覽**，然後按一下 [**SQL 資料庫**]。</span><span class="sxs-lookup"><span data-stu-id="c59b9-128">On the left banner, click to **BROWSE**, and then click **SQL databases**.</span></span>

3.  <span data-ttu-id="c59b9-129">利用左窗格中選取的 [**SQL 資料庫**]，按一下您的使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="c59b9-129">With **SQL databases** selected in the left pane, click your user database.</span></span>

4.  <span data-ttu-id="c59b9-130">在資料庫刀鋒視窗中，按一下 [所有設定] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c59b9-130">In the database blade, click **All settings**.</span></span>

5.  <span data-ttu-id="c59b9-131">在 [設定] \*\*\*\* 刀鋒視窗中，按一下 [透明資料加密 (預覽版)] \*\*\*\* 部分，以開啟 [透明資料加密 (預覽版)] \*\*\*\* 刀鋒視窗。</span><span class="sxs-lookup"><span data-stu-id="c59b9-131">In the **Settings** blade, click **Transparent data encryption (preview)** part to open the **Transparent data encryption PREVIEW** blade.</span></span> <span data-ttu-id="c59b9-132">若還未註冊 TDE 預覽版，資料加密設定將會停用，直到您完成註冊為止。</span><span class="sxs-lookup"><span data-stu-id="c59b9-132">If you have not already signed up for the TDE preview, the data encryption settings will be disabled until you complete signup.</span></span>

6.  <span data-ttu-id="c59b9-133">按一下 [預覽條款] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c59b9-133">Click **PREVIEW TERMS**.</span></span>

7.  <span data-ttu-id="c59b9-134">閱讀預覽的條款，如果您同意這些條款，請選取 [**透明資料 encryptionPreview 詞彙**] 核取方塊，然後按一下頁面底部附近的 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="c59b9-134">Read the terms of the preview, and if you agree to the terms, select the **Transparent Data encryptionPreview terms** check box, and then click **OK** near the bottom of the page.</span></span> <span data-ttu-id="c59b9-135">返回 [**資料 encryptionPREVIEW** ] 分頁，此時應該會啟用 [**資料加密**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c59b9-135">Returning to the **Data encryptionPREVIEW** blade, where the **Data encryption** button should now be enabled.</span></span>

8.  <span data-ttu-id="c59b9-136">在 [資料加密預覽] \*\*\*\* 刀鋒視窗中，將 [資料加密] \*\*\*\* 按鈕移至 [開啟] \*\*\*\*，然後按一下 [儲存] \*\*\*\* (位於頁面頂端)，以套用此設定。</span><span class="sxs-lookup"><span data-stu-id="c59b9-136">In the **Data encryption PREVIEW** blade, move the **Data encryption** button to **On**, and then click **Save** (at the top of the page) to apply the setting.</span></span> <span data-ttu-id="c59b9-137">[加密狀態] \*\*\*\* 會顯示透明資料加密的概略進度。</span><span class="sxs-lookup"><span data-stu-id="c59b9-137">The **Encryption status** will approximate the progress of the transparent data encryption.</span></span>

     <span data-ttu-id="c59b9-138">![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")</span><span class="sxs-lookup"><span data-stu-id="c59b9-138">![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")</span></span>

     <span data-ttu-id="c59b9-139">您也可以使用查詢工具 (例如 [!INCLUDE[ssSDS](../includes/sssds-md.md)] )，以具有 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] VIEW DATABASE STATE **權限的資料庫使用者身分，連接到** 監視加密進度。</span><span class="sxs-lookup"><span data-stu-id="c59b9-139">You can also monitor the progress of encryption by connecting to [!INCLUDE[ssSDS](../includes/sssds-md.md)] using a query tool such as [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] as a database user with the **VIEW DATABASE STATE** permission.</span></span> <span data-ttu-id="c59b9-140">查詢 `encryption_state` [sys.databases dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)視圖的資料行。</span><span class="sxs-lookup"><span data-stu-id="c59b9-140">Query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

##  <a name="enabling-tde-on-sssds-by-using-transact-sql"></a><a name="Encrypt"></a><span data-ttu-id="c59b9-141">使用 Transact-sql 啟用的 TDE [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c59b9-141">Enabling TDE on [!INCLUDE[ssSDS](../includes/sssds-md.md)] by Using Transact-SQL</span></span>
 <span data-ttu-id="c59b9-142">下列步驟中假設您已經註冊預覽版。</span><span class="sxs-lookup"><span data-stu-id="c59b9-142">The following steps, assume you have already signed up for the preview.</span></span>

###  <a name="TsqlProcedure"></a>

1.  <span data-ttu-id="c59b9-143">使用 master 資料庫中之 **dbmanager** 角色的系統管理員或成員身分的登入，連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="c59b9-143">Connect to the database using a login that is an administrator or a member of the **dbmanager** role in the master database.</span></span>

2.  <span data-ttu-id="c59b9-144">執行下列陳述式，以建立資料庫加密金鑰及加密資料庫。</span><span class="sxs-lookup"><span data-stu-id="c59b9-144">Execute the following statements to create a database encryption key and encrypt the database.</span></span>

    ```sql
    -- Create the database encryption key that will be used for TDE.
    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_256 
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;

    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;
    GO
    ```

3.  <span data-ttu-id="c59b9-145">若要監視的加密進度 [!INCLUDE[ssSDS](../includes/sssds-md.md)] ，具有**VIEW database STATE**許可權的資料庫使用者可以查詢 `encryption_state` [sys.databases dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)視圖的資料行。</span><span class="sxs-lookup"><span data-stu-id="c59b9-145">To monitor the progress of encryption on [!INCLUDE[ssSDS](../includes/sssds-md.md)], database users with the **VIEW DATABASE STATE** permission can query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

## <a name="enabling-tde-on-sql-database-by-using-powershell"></a><span data-ttu-id="c59b9-146">使用 PowerShell 啟用 SQL Database 的 TDE</span><span class="sxs-lookup"><span data-stu-id="c59b9-146">Enabling TDE on SQL Database by Using PowerShell</span></span>
 <span data-ttu-id="c59b9-147">您可以使用 Azure PowerShell，執行下列命令開啟/關閉 TDE。</span><span class="sxs-lookup"><span data-stu-id="c59b9-147">Using the Azure PowerShell you can run the following command to turn TDE on/off.</span></span> <span data-ttu-id="c59b9-148">您必須將您的帳戶連接到 PS 視窗，才能執行此命令。</span><span class="sxs-lookup"><span data-stu-id="c59b9-148">You do have to connect your account to the PS window before running the command.</span></span> <span data-ttu-id="c59b9-149">下列步驟中假設您已經註冊預覽版。</span><span class="sxs-lookup"><span data-stu-id="c59b9-149">The following steps, assume you have already signed up for the preview.</span></span> <span data-ttu-id="c59b9-150">如需 PowerShell 的其他相關資訊，請參閱 [如何安裝及設定 Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/)。</span><span class="sxs-lookup"><span data-stu-id="c59b9-150">For additional information about PowerShell, see [How to install and configure Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).</span></span>

1.  <span data-ttu-id="c59b9-151">啟用 TDE、傳回 TDE 狀態及檢視加密活動。</span><span class="sxs-lookup"><span data-stu-id="c59b9-151">To enable TDE, return the TDE status, and view the encryption activity.</span></span>

    ```powershell
    Switch-AzureMode -Name AzureResourceManager
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"

    Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    ```

2.  <span data-ttu-id="c59b9-152">若要停用 TDE：</span><span class="sxs-lookup"><span data-stu-id="c59b9-152">To disable TDE:</span></span>

    ```powershell
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"
    Switch-AzureMode -Name AzureServiceManagement
    ```

##  <a name="decrypting-a-tde-protected-database-on-sssds"></a><a name="Decrypt"></a><span data-ttu-id="c59b9-153">解密上受 TDE 保護的資料庫[!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c59b9-153">Decrypting a TDE Protected Database on [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span></span>

#### <a name="to-disable-tde-by-using-the-azure-portal"></a><span data-ttu-id="c59b9-154">使用 Azure 入口網站停用 TDE</span><span class="sxs-lookup"><span data-stu-id="c59b9-154">To Disable TDE by Using the Azure Portal</span></span>

1.  <span data-ttu-id="c59b9-155">請造訪 Azure 入口網站 [https://portal.azure.com](https://portal.azure.com) ，並使用您的 Azure 系統管理員或參與者帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c59b9-155">Visit the Azure Portal at [https://portal.azure.com](https://portal.azure.com) and sign-in with your Azure Administrator or Contributor account.</span></span>

2.  <span data-ttu-id="c59b9-156">在左邊的橫幅中，按一下以**瀏覽**，然後按一下 [**SQL 資料庫**]。</span><span class="sxs-lookup"><span data-stu-id="c59b9-156">On the left banner, click to **BROWSE**, and then click **SQL databases**.</span></span>

3.  <span data-ttu-id="c59b9-157">利用左窗格中選取的 [**SQL 資料庫**]，按一下您的使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="c59b9-157">With **SQL databases** selected in the left pane, click your user database.</span></span>

4.  <span data-ttu-id="c59b9-158">在資料庫刀鋒視窗中，按一下 [所有設定] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c59b9-158">In the database blade, click **All settings**.</span></span>

5.  <span data-ttu-id="c59b9-159">在 [設定] \*\*\*\* 刀鋒視窗中，按一下 [透明資料加密 (預覽版)] \*\*\*\* 部分，以開啟 [透明資料加密 (預覽版)] \*\*\*\* 刀鋒視窗。</span><span class="sxs-lookup"><span data-stu-id="c59b9-159">In the **Settings** blade, click **Transparent data encryption (preview)** part to open the **Transparent data encryption PREVIEW** blade.</span></span>

6.  <span data-ttu-id="c59b9-160">在 [透明資料加密預覽] \*\*\*\* 刀鋒視窗中，將 [資料加密] \*\*\*\* 按鈕移至 [關閉] \*\*\*\*，然後按一下 [儲存] \*\*\*\* (位於頁面頂端)，以套用此設定。</span><span class="sxs-lookup"><span data-stu-id="c59b9-160">In the **Transparent data encryption PREVIEW** blade, move the **Data encryption** button to **Off**, and then click **Save** (at the top of the page) to apply the setting.</span></span> <span data-ttu-id="c59b9-161">[加密狀態] \*\*\*\* 會顯示透明資料解密的概略進度。</span><span class="sxs-lookup"><span data-stu-id="c59b9-161">The **Encryption status** will approximate the progress of the transparent data decryption.</span></span>

     <span data-ttu-id="c59b9-162">您也可以使用查詢工具 (例如 [!INCLUDE[ssSDS](../includes/sssds-md.md)] )，以具有 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] VIEW DATABASE STATE **權限的資料庫使用者身分，連接到** 監視解密進度。</span><span class="sxs-lookup"><span data-stu-id="c59b9-162">You can also monitor the progress of decryption by connecting to [!INCLUDE[ssSDS](../includes/sssds-md.md)] using a query tool such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] as a database user with the **VIEW DATABASE STATE** permission.</span></span> <span data-ttu-id="c59b9-163">查詢 `encryption_state` [sys.databases dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)視圖的資料行。</span><span class="sxs-lookup"><span data-stu-id="c59b9-163">Query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)view.</span></span>

#### <a name="to-disable-tde-by-using-transact-sql"></a><span data-ttu-id="c59b9-164">使用 TRANSACT-SQL 停用 TDE</span><span class="sxs-lookup"><span data-stu-id="c59b9-164">To Disable TDE by Using Transact-SQL</span></span>

1.  <span data-ttu-id="c59b9-165">使用 master 資料庫中之 **dbmanager** 角色的系統管理員或成員身分的登入，連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="c59b9-165">Connect to the database using a login that is an administrator or a member of the **dbmanager** role in the master database.</span></span>

2.  <span data-ttu-id="c59b9-166">執行下列陳述式，以解密資料庫。</span><span class="sxs-lookup"><span data-stu-id="c59b9-166">Execute the following statements to decrypt the database.</span></span>

    ```sql
    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;
    GO
    ```

3.  <span data-ttu-id="c59b9-167">若要監視的加密進度 [!INCLUDE[ssSDS](../includes/sssds-md.md)] ，具有**VIEW database STATE**許可權的資料庫使用者可以查詢 `encryption_state` [sys.databases dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)視圖的資料行。</span><span class="sxs-lookup"><span data-stu-id="c59b9-167">To monitor the progress of encryption on [!INCLUDE[ssSDS](../includes/sssds-md.md)], database users with the **VIEW DATABASE STATE** permission can query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

##  <a name="working-with-tde-protected-databases-on-sssds"></a><a name="Working"></a><span data-ttu-id="c59b9-168">使用上的 TDE 受保護資料庫[!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c59b9-168">Working with TDE Protected Databases on [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span></span>
 <span data-ttu-id="c59b9-169">您無須解密資料庫，即可在 Azure 執行作業。</span><span class="sxs-lookup"><span data-stu-id="c59b9-169">You do not need to decrypt databases for operations within Azure.</span></span> <span data-ttu-id="c59b9-170">目標會自動繼承來源資料庫或主要資料庫的 TDE 設定。</span><span class="sxs-lookup"><span data-stu-id="c59b9-170">The TDE settings on the source database or primary database are transparently inherited on the target.</span></span> <span data-ttu-id="c59b9-171">這包括下列作業：</span><span class="sxs-lookup"><span data-stu-id="c59b9-171">This includes operations involving:</span></span>

-   <span data-ttu-id="c59b9-172">異地複原</span><span class="sxs-lookup"><span data-stu-id="c59b9-172">Geo-Restore</span></span>

-   <span data-ttu-id="c59b9-173">自助時間點還原</span><span class="sxs-lookup"><span data-stu-id="c59b9-173">Self-Service Point in Time Restore</span></span>

-   <span data-ttu-id="c59b9-174">還原已刪除的資料庫</span><span class="sxs-lookup"><span data-stu-id="c59b9-174">Restore a Deleted Database</span></span>

-   <span data-ttu-id="c59b9-175">使用中的異地複寫</span><span class="sxs-lookup"><span data-stu-id="c59b9-175">Active Geo_Replication</span></span>

-   <span data-ttu-id="c59b9-176">建立資料庫複本</span><span class="sxs-lookup"><span data-stu-id="c59b9-176">Creating a Database Copy</span></span>

##  <a name="moving-a-tde-protected-database-on-using-bacpac-files"></a><a name="Moving"></a><span data-ttu-id="c59b9-177">使用在上移動 TDE 保護的資料庫。Bacpac 檔案</span><span class="sxs-lookup"><span data-stu-id="c59b9-177">Moving a TDE Protected Database on using .Bacpac Files</span></span>
 <span data-ttu-id="c59b9-178">在 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] 入口網站使用 [匯出資料庫] 功能或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的 [匯入和匯出精靈] 匯出受 TDE 保護的資料庫時，資料庫內容不會加密。</span><span class="sxs-lookup"><span data-stu-id="c59b9-178">When exporting a TDE protected database using the Export Database function in the [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] Portal or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard, the content of the database is not encrypted.</span></span> <span data-ttu-id="c59b9-179">該內容會儲存在未加密的 .bacpac 檔案中。</span><span class="sxs-lookup"><span data-stu-id="c59b9-179">The content is stored in .bacpac files which are not encrypted.</span></span>  <span data-ttu-id="c59b9-180">請務必為 .bacpac 檔案施以適當的保護措施，並在匯入新資料庫作業完成時，立即啟用 TDE。</span><span class="sxs-lookup"><span data-stu-id="c59b9-180">Be sure to protect the .bacpac files appropriately and enable TDE once import of the new database is completed.</span></span>

## <a name="related-sql-server-topic"></a><span data-ttu-id="c59b9-181">相關的 SQL Server 主題</span><span class="sxs-lookup"><span data-stu-id="c59b9-181">Related SQL Server Topic</span></span>
 [<span data-ttu-id="c59b9-182">使用 EKM 啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="c59b9-182">Enable TDE Using EKM</span></span>](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)

## <a name="see-also"></a><span data-ttu-id="c59b9-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c59b9-183">See Also</span></span>
 <span data-ttu-id="c59b9-184">[透明資料加密 &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [建立認證 &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [建立非對稱金鑰 &#40;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) transact-sql&#41;[建立資料庫加密金鑰](/sql/t-sql/statements/create-database-encryption-key-transact-sql)&#40;TRANSACT-SQL&#41;[alter Database &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql) [alter database SET 選項 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)</span><span class="sxs-lookup"><span data-stu-id="c59b9-184">[Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql) [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)</span></span>
