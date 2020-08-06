---
title: 使用 EKM 啟用 TDE |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], TDE using an EKM
- TDE, EKM how to
- EKM, TDE how to
- Transparent Data Encryption, using EKM
ms.assetid: b892e7a7-95bd-4903-bf54-55ce08e225af
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: e659c5ff0245fdb17192b845eafc60badf5e295e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709070"
---
# <a name="enable-tde-using-ekm"></a><span data-ttu-id="064ac-102">使用 EKM 啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="064ac-102">Enable TDE Using EKM</span></span>
  <span data-ttu-id="064ac-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中透過使用儲存在可延伸金鑰管理 (EKM) 模組中的非對稱金鑰，啟用透明資料加密 (TDE) 以保護資料庫加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="064ac-103">This topic describes how to enable transparent data encryption (TDE) in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] to protect a database encryption key by using an asymmetric key stored in an extensible key management (EKM) module with [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="064ac-104">TDE 會使用稱為資料庫加密金鑰的對稱金鑰來加密整個資料庫的儲存體。</span><span class="sxs-lookup"><span data-stu-id="064ac-104">TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key.</span></span> <span data-ttu-id="064ac-105">也可以使用憑證來保護資料庫加密金鑰，該憑證是由 master 資料庫的資料庫主要金鑰所保護。</span><span class="sxs-lookup"><span data-stu-id="064ac-105">The database encryption key can also be protected using a certificate which is protected by the database master key of the master database.</span></span> <span data-ttu-id="064ac-106">如需有關使用資料庫主要金鑰來保護資料庫加密金鑰的詳細資訊，請參閱[透明資料加密 &#40;TDE&#41;](transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="064ac-106">For more information about protecting the database encryption key by using the database master key, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span> <span data-ttu-id="064ac-107">如需 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在 Azure VM 上執行時設定 TDE 的相關資訊，請參閱[使用 Azure 金鑰保存庫進行可延伸金鑰管理 &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="064ac-107">For information about configuring TDE when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running on an Azure VM, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
 <span data-ttu-id="064ac-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="064ac-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="064ac-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="064ac-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="064ac-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="064ac-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="064ac-111">安全性</span><span class="sxs-lookup"><span data-stu-id="064ac-111">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="064ac-112">若要使用 Transact-SQL 透過 EKM 啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="064ac-112">To enable TDE using EKM, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="064ac-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="064ac-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="064ac-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="064ac-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="064ac-115">您必須是高權限使用者 (如系統管理員) 才能建立資料庫加密金鑰及加密資料庫。</span><span class="sxs-lookup"><span data-stu-id="064ac-115">You must be a high privileged user (such as a system administrator) to create a database encryption key and encrypt a database.</span></span> <span data-ttu-id="064ac-116">該使用者必須能夠由 EKM 模組來驗證。</span><span class="sxs-lookup"><span data-stu-id="064ac-116">That user must be able to be authenticated by the EKM module.</span></span>  
  
-   <span data-ttu-id="064ac-117">一啟動時， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 就必須開啟資料庫。</span><span class="sxs-lookup"><span data-stu-id="064ac-117">Upon start up the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must open the database.</span></span> <span data-ttu-id="064ac-118">若要這樣做，您應該建立要由 EKM 所驗證的認證，並將它加入到根據非對稱金鑰的登入中。</span><span class="sxs-lookup"><span data-stu-id="064ac-118">To do this, you should create a credential that will be authenticated by the EKM, and add it to a login that is based on an asymmetric key.</span></span> <span data-ttu-id="064ac-119">使用者無法使用該登入來進行登入，但是 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 將能夠使用 EKM 裝置來驗證本身。</span><span class="sxs-lookup"><span data-stu-id="064ac-119">Users cannot login using that login, but the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] will be able to authenticate itself with the EKM device.</span></span>  
  
-   <span data-ttu-id="064ac-120">如果遺失了 EKM 模組內所儲存的非對稱金鑰， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]將無法開啟資料庫。</span><span class="sxs-lookup"><span data-stu-id="064ac-120">If the asymmetric key stored in the EKM module is lost, the database will not be able to be opened by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="064ac-121">如果 EKM 提供者可讓您備份非對稱金鑰，您應該建立備份，並將它儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="064ac-121">If the EKM provider lets you back up the asymmetric key, you should create a back up and store it in a secure location.</span></span>  
  
-   <span data-ttu-id="064ac-122">您的 EKM 提供者所需的選項和參數可能不同於以下程式碼範例中所提供的選項和參數。</span><span class="sxs-lookup"><span data-stu-id="064ac-122">The options and parameters required by your EKM provider can differ from what is provided in the code example below.</span></span> <span data-ttu-id="064ac-123">如需詳細資訊，請洽詢 EKM 提供者。</span><span class="sxs-lookup"><span data-stu-id="064ac-123">For more information, see your EKM provider.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="064ac-124">Security</span><span class="sxs-lookup"><span data-stu-id="064ac-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="064ac-125">權限</span><span class="sxs-lookup"><span data-stu-id="064ac-125">Permissions</span></span>  
 <span data-ttu-id="064ac-126">此主題會使用以下權限：</span><span class="sxs-lookup"><span data-stu-id="064ac-126">This topic uses the following permissions:</span></span>  
  
-   <span data-ttu-id="064ac-127">若要變更組態選項及執行 RECONFIGURE 陳述式，您必須取得 ALTER SETTINGS 伺服器層級的權限。</span><span class="sxs-lookup"><span data-stu-id="064ac-127">To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="064ac-128">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="064ac-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
-   <span data-ttu-id="064ac-129">需要 ALTER ANY CREDENTIAL 權限。</span><span class="sxs-lookup"><span data-stu-id="064ac-129">Requires ALTER ANY CREDENTIAL permission.</span></span>  
  
-   <span data-ttu-id="064ac-130">需要 ALTER ANY LOGIN 權限。</span><span class="sxs-lookup"><span data-stu-id="064ac-130">Requires ALTER ANY LOGIN permission.</span></span>  
  
-   <span data-ttu-id="064ac-131">需要 CREATE ASYMMETRIC KEY 權限。</span><span class="sxs-lookup"><span data-stu-id="064ac-131">Requires CREATE ASYMMETRIC KEY permission.</span></span>  
  
-   <span data-ttu-id="064ac-132">需要資料庫的 CONTROL 權限才能加密資料庫。</span><span class="sxs-lookup"><span data-stu-id="064ac-132">Requires CONTROL permission on the database to encrypt the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="064ac-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="064ac-133">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-tde-using-ekm"></a><span data-ttu-id="064ac-134">若要使用 EKM 啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="064ac-134">To enable TDE using EKM</span></span>  
  
1.  <span data-ttu-id="064ac-135">將 EKM 提供者提供的檔案複製到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 電腦上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="064ac-135">Copy the files supplied by the EKM provider to an appropriate location on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="064ac-136">在此範例中，我們使用 **C:\EKM** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="064ac-136">In this example, we use the **C:\EKM** folder.</span></span>  
  
2.  <span data-ttu-id="064ac-137">依照 EKM 提供者的要求將憑證安裝到電腦上。</span><span class="sxs-lookup"><span data-stu-id="064ac-137">Install certificates to the computer as required by your EKM provider.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="064ac-138">未提供 EKM 提供者。</span><span class="sxs-lookup"><span data-stu-id="064ac-138">does not supply an EKM provider.</span></span> <span data-ttu-id="064ac-139">每一個 EKM 提供者都會有安裝、設定及授權使用者的不同程序。</span><span class="sxs-lookup"><span data-stu-id="064ac-139">Each EKM provider can have different procedures for installing, configuring and authorizing users.</span></span>  <span data-ttu-id="064ac-140">請參閱 EKM 提供者文件集來完成這個步驟。</span><span class="sxs-lookup"><span data-stu-id="064ac-140">Consult your EKM provider documentation to complete this step.</span></span>  
  
3.  <span data-ttu-id="064ac-141">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="064ac-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
4.  <span data-ttu-id="064ac-142">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="064ac-142">On the Standard bar, click **New Query**.</span></span>  
  
5.  <span data-ttu-id="064ac-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="064ac-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Enable advanced options.  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Create a cryptographic provider, which we have chosen to call "EKM_Prov," based on an EKM provider  
  
    CREATE CRYPTOGRAPHIC PROVIDER EKM_Prov   
    FROM FILE = 'C:\EKM_Files\KeyProvFile.dll' ;  
    GO  
  
    -- Create a credential that will be used by system administrators.  
    CREATE CREDENTIAL sa_ekm_tde_cred   
    WITH IDENTITY = 'Identity1',   
    SECRET = 'q*gtev$0u#D1v'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
    GO  
  
    -- Add the credential to a high privileged user such as your   
    -- own domain login in the format [DOMAIN\login].  
    ALTER LOGIN Contoso\Mary  
    ADD CREDENTIAL sa_ekm_tde_cred ;  
    GO  
    -- create an asymmetric key stored inside the EKM provider  
    USE master ;  
    GO  
    CREATE ASYMMETRIC KEY ekm_login_key   
    FROM PROVIDER [EKM_Prov]  
    WITH ALGORITHM = RSA_512,  
    PROVIDER_KEY_NAME = 'SQL_Server_Key' ;  
    GO  
  
    -- Create a credential that will be used by the Database Engine.  
    CREATE CREDENTIAL ekm_tde_cred   
    WITH IDENTITY = 'Identity2'   
    , SECRET = 'jeksi84&sLksi01@s'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
  
    -- Add a login used by TDE, and add the new credential to the login.  
    CREATE LOGIN EKM_Login   
    FROM ASYMMETRIC KEY ekm_login_key ;  
    GO  
    ALTER LOGIN EKM_Login   
    ADD CREDENTIAL ekm_tde_cred ;  
    GO  
  
    -- Create the database encryption key that will be used for TDE.  
    USE AdventureWorks2012 ;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM  = AES_128  
    ENCRYPTION BY SERVER ASYMMETRIC KEY ekm_login_key ;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE AdventureWorks2012   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
 <span data-ttu-id="064ac-144">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="064ac-144">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="064ac-145">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-145">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [<span data-ttu-id="064ac-146">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-146">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)  
  
-   [<span data-ttu-id="064ac-147">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-147">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [<span data-ttu-id="064ac-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)  
  
-   [<span data-ttu-id="064ac-149">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-149">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
-   [<span data-ttu-id="064ac-150">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-150">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [<span data-ttu-id="064ac-151">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-151">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)  
  
-   [<span data-ttu-id="064ac-152">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-152">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [<span data-ttu-id="064ac-153">使用 Azure 金鑰保存庫進行可延伸金鑰管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="064ac-153">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
-   [<span data-ttu-id="064ac-154">Azure SQL Database 的透明資料加密</span><span class="sxs-lookup"><span data-stu-id="064ac-154">Transparent Data Encryption with Azure SQL Database</span></span>](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)  
  
  
