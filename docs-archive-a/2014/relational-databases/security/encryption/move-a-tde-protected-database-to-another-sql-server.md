---
title: 將 TDE 保護的資料庫移至另一個 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, moving
- TDE, moving a database
ms.assetid: fb420903-df54-4016-bab6-49e6dfbdedc7
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b03b4d9ecf31e9953fd3e22cec5c51bbacc0c25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710529"
---
# <a name="move-a-tde-protected-database-to-another-sql-server"></a><span data-ttu-id="02d06-102">將 TDE 保護的資料庫移至另一個 SQL Server</span><span class="sxs-lookup"><span data-stu-id="02d06-102">Move a TDE Protected Database to Another SQL Server</span></span>
  <span data-ttu-id="02d06-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../../includes/tsql-md.md)]，透過透明資料加密 (TDE) 保護資料庫，然後將資料庫移到另一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="02d06-103">This topic describes how to protect a database by using transparent data encryption (TDE), and then move the database to another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="02d06-104">TDE 會執行資料和記錄檔的即時 I/O 加密和解密。</span><span class="sxs-lookup"><span data-stu-id="02d06-104">TDE performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="02d06-105">加密會使用資料庫加密金鑰 (DEK)，此金鑰會儲存在資料庫開機記錄中，以在復原期間提供可用性。</span><span class="sxs-lookup"><span data-stu-id="02d06-105">The encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="02d06-106">DEK 是對稱金鑰，而其維護安全的方式是使用儲存於伺服器之 `master` 資料庫內的憑證或是受到 EKM 模組所保護的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="02d06-106">The DEK is a symmetric key secured by using a certificate stored in the `master` database of the server or an asymmetric key protected by an EKM module.</span></span>  
  
 <span data-ttu-id="02d06-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="02d06-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="02d06-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="02d06-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="02d06-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="02d06-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="02d06-110">安全性</span><span class="sxs-lookup"><span data-stu-id="02d06-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="02d06-111">**若要使用下列項目，建立透明資料加密所保護的資料庫：**</span><span class="sxs-lookup"><span data-stu-id="02d06-111">**To create a database protected by transparent data encryption, using:**</span></span>  
  
     [<span data-ttu-id="02d06-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="02d06-112">SQL Server Management Studio</span></span>](#SSMSCreate)  
  
     [<span data-ttu-id="02d06-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="02d06-113">Transact-SQL</span></span>](#TsqlCreate)  
  
-   <span data-ttu-id="02d06-114">**若要使用下列項目移動資料庫：**</span><span class="sxs-lookup"><span data-stu-id="02d06-114">**To move a database, using:**</span></span>  
  
     [<span data-ttu-id="02d06-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="02d06-115">SQL Server Management Studio</span></span>](#SSMSMove)  
  
     [<span data-ttu-id="02d06-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="02d06-116">Transact-SQL</span></span>](#TsqlMove)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="02d06-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="02d06-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="02d06-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="02d06-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="02d06-119">移動 TDE 保護的資料庫時，您也必須移動用來開啟 DEK 的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="02d06-119">When moving a TDE protected database, you must also move the certificate or asymmetric key that is used to open the DEK.</span></span> <span data-ttu-id="02d06-120">憑證或非對稱金鑰必須安裝在 `master` 目的地伺服器的資料庫中， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 才能存取資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="02d06-120">The certificate or asymmetric key must be installed in the `master` database of the destination server, so that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can access the database files.</span></span> <span data-ttu-id="02d06-121">如需詳細資訊，請參閱[透明資料加密 &#40;TDE&#41;](transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="02d06-121">For more information, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span>  
  
-   <span data-ttu-id="02d06-122">您必須同時保留憑證檔案和私密金鑰檔案的副本，才能復原憑證。</span><span class="sxs-lookup"><span data-stu-id="02d06-122">You must retain copies of both the certificate file and the private key file in order to recover the certificate.</span></span> <span data-ttu-id="02d06-123">私密金鑰的密碼不必與資料庫主要金鑰密碼相同。</span><span class="sxs-lookup"><span data-stu-id="02d06-123">The password for the private key does not have to be the same as the database master key password.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="02d06-124">將此處建立的檔案儲存在**C:\Program FILES\MICROSOFT SQL Server\MSSQL12。** 預設為 MSSQLSERVER\MSSQL\DATA。</span><span class="sxs-lookup"><span data-stu-id="02d06-124">stores the files created here in **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA** by default.</span></span> <span data-ttu-id="02d06-125">您的檔案名稱和位置可能會不同。</span><span class="sxs-lookup"><span data-stu-id="02d06-125">Your file names and locations might be different.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="02d06-126">Security</span><span class="sxs-lookup"><span data-stu-id="02d06-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="02d06-127">權限</span><span class="sxs-lookup"><span data-stu-id="02d06-127">Permissions</span></span>  
  
-   <span data-ttu-id="02d06-128">需要 `CONTROL DATABASE` 資料庫的許可權 `master` ，才能建立資料庫主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="02d06-128">Requires `CONTROL DATABASE` permission on the `master` database to create the database master key.</span></span>  
  
-   <span data-ttu-id="02d06-129">需要 `CREATE CERTIFICATE` 資料庫的許可權 `master` ，才能建立保護 DEK 的憑證。</span><span class="sxs-lookup"><span data-stu-id="02d06-129">Requires `CREATE CERTIFICATE` permission on the `master` database to create the certificate that protects the DEK.</span></span>  
  
-   <span data-ttu-id="02d06-130">需要加密資料庫的 `CONTROL DATABASE` 權限，以及用於加密資料庫加密金鑰之憑證或非對稱金鑰的 `VIEW DEFINITION` 權限。</span><span class="sxs-lookup"><span data-stu-id="02d06-130">Requires `CONTROL DATABASE` permission on the encrypted database and `VIEW DEFINITION` permission on the certificate or asymmetric key that is used to encrypt the database encryption key.</span></span>  
  
##  <a name="to-create-a-database-protected-by-transparent-data-encryption"></a><a name="SSMSProcedure"></a> <span data-ttu-id="02d06-131">建立透明資料加密所保護的資料庫</span><span class="sxs-lookup"><span data-stu-id="02d06-131">To create a database protected by transparent data encryption</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSCreate"></a> <span data-ttu-id="02d06-132">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="02d06-132">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="02d06-133">在資料庫中建立資料庫主要金鑰和憑證 `master` 。</span><span class="sxs-lookup"><span data-stu-id="02d06-133">Create a database master key and certificate in the `master` database.</span></span> <span data-ttu-id="02d06-134">如需詳細資訊，請參閱下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-134">For more information, see **Using Transact-SQL** below.</span></span>  
  
2.  <span data-ttu-id="02d06-135">在資料庫中建立伺服器憑證的備份 `master` 。</span><span class="sxs-lookup"><span data-stu-id="02d06-135">Create a backup of the server certificate in the `master` database.</span></span> <span data-ttu-id="02d06-136">如需詳細資訊，請參閱下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-136">For more information, see **Using Transact-SQL** below.</span></span>  
  
3.  <span data-ttu-id="02d06-137">在 [物件總管] 中，以滑鼠右鍵按一下 **[資料庫]** 資料夾，並選取 **[新增資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-137">In Object Explorer, right-click the **Databases** folder and select **New Database**.</span></span>  
  
4.  <span data-ttu-id="02d06-138">在 **[新增資料庫]** 對話方塊的 **[資料庫名稱]** 方塊中，輸入新資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="02d06-138">In the **New Database** dialog box, in the **Database name** box, enter the name of the new database.</span></span>  
  
5.  <span data-ttu-id="02d06-139">在 **[擁有者]** 方塊中，輸入新資料庫擁有者的名稱。</span><span class="sxs-lookup"><span data-stu-id="02d06-139">In the **Owner** box, enter the name of the new database's owner.</span></span> <span data-ttu-id="02d06-140">或者，按一下省略符號 **(...)** ，開啟 [選取資料庫擁有者] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="02d06-140">Alternately, click the ellipsis **(...)** to open the **Select Database Owner** dialog box.</span></span> <span data-ttu-id="02d06-141">如需有關建立新資料庫的詳細資訊，請參閱＜ [Create a Database](../../databases/create-a-database.md)＞。</span><span class="sxs-lookup"><span data-stu-id="02d06-141">For more information on creating a new database, see [Create a Database](../../databases/create-a-database.md).</span></span>  
  
6.  <span data-ttu-id="02d06-142">在 [物件總管] 中，按一下加號展開 **[資料庫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="02d06-142">In Object Explorer, click the plus sign to expand the **Databases** folder.</span></span>  
  
7.  <span data-ttu-id="02d06-143">以滑鼠右鍵按一下建立的資料庫，指向 **[工作]** ，然後選取 **[管理資料庫加密]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-143">Right-click the database you created, point to **Tasks**, and select **Manage Database Encryption**.</span></span>  
  
     <span data-ttu-id="02d06-144">**[管理資料庫加密]** 對話方塊有下列選項。</span><span class="sxs-lookup"><span data-stu-id="02d06-144">The following options are available on the **Manage Database Encryption** dialog box.</span></span>  
  
     <span data-ttu-id="02d06-145">**加密演算法**</span><span class="sxs-lookup"><span data-stu-id="02d06-145">**Encryption Algorithm**</span></span>  
     <span data-ttu-id="02d06-146">顯示或設定要用於資料庫加密的演算法。</span><span class="sxs-lookup"><span data-stu-id="02d06-146">Displays or sets the algorithm to use for database encryption.</span></span> <span data-ttu-id="02d06-147">`AES128` 是預設演算法。</span><span class="sxs-lookup"><span data-stu-id="02d06-147">`AES128` is the default algorithm.</span></span> <span data-ttu-id="02d06-148">這個欄位不能空白。</span><span class="sxs-lookup"><span data-stu-id="02d06-148">This field cannot be blank.</span></span> <span data-ttu-id="02d06-149">如需有關加密演算法的詳細資訊，請參閱＜ [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md)＞。</span><span class="sxs-lookup"><span data-stu-id="02d06-149">For more information on encryption algorithms, see [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md).</span></span>  
  
     <span data-ttu-id="02d06-150">**使用伺服器憑證**</span><span class="sxs-lookup"><span data-stu-id="02d06-150">**Use server certificate**</span></span>  
     <span data-ttu-id="02d06-151">設定由憑證維護安全的加密。</span><span class="sxs-lookup"><span data-stu-id="02d06-151">Sets the encryption to be secured by a certificate.</span></span> <span data-ttu-id="02d06-152">從清單中選取一項。</span><span class="sxs-lookup"><span data-stu-id="02d06-152">Select one from the list.</span></span> <span data-ttu-id="02d06-153">如果您沒有伺服器憑證的 `VIEW DEFINITION` 權限，此清單將會是空的。</span><span class="sxs-lookup"><span data-stu-id="02d06-153">If you do not have the `VIEW DEFINITION` permission on server certificates, this list will be empty.</span></span> <span data-ttu-id="02d06-154">如果選取了憑證方法的加密，這個值就不能是空的。</span><span class="sxs-lookup"><span data-stu-id="02d06-154">If a certificate method of encryption is selected, this value cannot be empty.</span></span> <span data-ttu-id="02d06-155">如需有關憑證的詳細資訊，請參閱＜ [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)＞。</span><span class="sxs-lookup"><span data-stu-id="02d06-155">For more information about certificates, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
     <span data-ttu-id="02d06-156">**使用伺服器非對稱金鑰**</span><span class="sxs-lookup"><span data-stu-id="02d06-156">**Use server asymmetric key**</span></span>  
     <span data-ttu-id="02d06-157">設定由非對稱金鑰維護安全的加密。</span><span class="sxs-lookup"><span data-stu-id="02d06-157">Sets the encryption to be secured by an asymmetric key.</span></span> <span data-ttu-id="02d06-158">只會顯示可用的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="02d06-158">Only available asymmetric keys are displayed.</span></span> <span data-ttu-id="02d06-159">受到 EKM 模組所保護的非對稱金鑰可以使用 TDE 加密資料庫。</span><span class="sxs-lookup"><span data-stu-id="02d06-159">Only an asymmetric key protected by an EKM module can encrypt a database using TDE.</span></span>  
  
     <span data-ttu-id="02d06-160">**將資料庫加密設為開啟**</span><span class="sxs-lookup"><span data-stu-id="02d06-160">**Set Database Encryption On**</span></span>  
     <span data-ttu-id="02d06-161">將資料庫改變為開啟 (核取) 或關閉 (不核取) TDE。</span><span class="sxs-lookup"><span data-stu-id="02d06-161">Alters the database to turn on (checked) or turn off (unchecked) TDE.</span></span>  
  
8.  <span data-ttu-id="02d06-162">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-162">When finished, click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlCreate"></a> <span data-ttu-id="02d06-163">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="02d06-163">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="02d06-164">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="02d06-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="02d06-165">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="02d06-166">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Create a database master key and a certificate in the master database.  
    USE master ;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    CREATE CERTIFICATE TestSQLServerCert   
    WITH SUBJECT = 'Certificate to protect TDE key'  
    GO  
    -- Create a backup of the server certificate in the master database.  
    -- The following code stores the backup of the certificate and the private key file in the default data location for this instance of SQL Server   
    -- (C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA).  
  
    BACKUP CERTIFICATE TestSQLServerCert   
    TO FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Create a database to be protected by TDE.  
    CREATE DATABASE CustRecords ;  
    GO  
    -- Switch to the new database.  
    -- Create a database encryption key, that is protected by the server certificate in the master database.   
    -- Alter the new database to encrypt the database using TDE.  
    USE CustRecords;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM = AES_128  
    ENCRYPTION BY SERVER CERTIFICATE TestSQLServerCert;  
    GO  
    ALTER DATABASE CustRecords  
    SET ENCRYPTION ON;  
    GO  
    ```  
  
 <span data-ttu-id="02d06-167">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="02d06-167">For more information, see:</span></span>  
  
-   [<span data-ttu-id="02d06-168">CREATE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-168">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="02d06-169">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-169">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="02d06-170">BACKUP CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-170">BACKUP CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-certificate-transact-sql)  
  
-   [<span data-ttu-id="02d06-171">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-171">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="02d06-172">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-172">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [<span data-ttu-id="02d06-173">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-173">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
##  <a name="to-move-a-database"></a><a name="TsqlProcedure"></a><span data-ttu-id="02d06-174">若要移動資料庫</span><span class="sxs-lookup"><span data-stu-id="02d06-174">To move a database</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSMove"></a> <span data-ttu-id="02d06-175">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="02d06-175">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="02d06-176">在 [物件總管] 中，以滑鼠右鍵按一下上方加密的資料庫，指向 [工作] ，然後選取 [卸離...]。</span><span class="sxs-lookup"><span data-stu-id="02d06-176">In Object Explorer, right-click the database you encrypted above, point to **Tasks** and select **Detach...**.</span></span>  
  
     <span data-ttu-id="02d06-177">**[卸離資料庫]** 對話方塊有下列選項。</span><span class="sxs-lookup"><span data-stu-id="02d06-177">The following options are available in the **Detach Database** dialog box.</span></span>  
  
     <span data-ttu-id="02d06-178">**要卸離的資料庫**</span><span class="sxs-lookup"><span data-stu-id="02d06-178">**Databases to detach**</span></span>  
     <span data-ttu-id="02d06-179">列出要卸離的資料庫。</span><span class="sxs-lookup"><span data-stu-id="02d06-179">Lists the databases to detach.</span></span>  
  
     <span data-ttu-id="02d06-180">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="02d06-180">**Database Name**</span></span>  
     <span data-ttu-id="02d06-181">顯示要卸離的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="02d06-181">Displays the name of the database to be detached.</span></span>  
  
     <span data-ttu-id="02d06-182">**卸除連接**</span><span class="sxs-lookup"><span data-stu-id="02d06-182">**Drop Connections**</span></span>  
     <span data-ttu-id="02d06-183">中斷到指定資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="02d06-183">Disconnect connections to the specified database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="02d06-184">您無法卸離具有使用中連接的資料庫。</span><span class="sxs-lookup"><span data-stu-id="02d06-184">You cannot detach a database with active connections.</span></span>  
  
     <span data-ttu-id="02d06-185">**更新統計資料**</span><span class="sxs-lookup"><span data-stu-id="02d06-185">**Update Statistics**</span></span>  
     <span data-ttu-id="02d06-186">依預設，卸離作業會在卸離資料庫時保留任何過時的最佳化統計資料。若要更新現有的最佳化統計資料，請按一下此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="02d06-186">By default, the detach operation retains any out-of-date optimization statistics when detaching the database; to update the existing optimization statistics, click this check box.</span></span>  
  
     <span data-ttu-id="02d06-187">**保留全文檢索目錄**</span><span class="sxs-lookup"><span data-stu-id="02d06-187">**Keep Full-Text Catalogs**</span></span>  
     <span data-ttu-id="02d06-188">依預設，卸離作業會保留與該資料庫關聯的所有全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="02d06-188">By default, the detach operation keeps any full-text catalogs that are associated with the database.</span></span> <span data-ttu-id="02d06-189">若要移除這些全文檢索目錄，請清除 **[保留全文檢索目錄]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="02d06-189">To remove them, clear the **Keep Full-Text Catalogs** check box.</span></span> <span data-ttu-id="02d06-190">只有當您從 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]升級資料庫時，才會出現這個選項。</span><span class="sxs-lookup"><span data-stu-id="02d06-190">This option appears only when you are upgrading a database from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="02d06-191">**狀態**</span><span class="sxs-lookup"><span data-stu-id="02d06-191">**Status**</span></span>  
     <span data-ttu-id="02d06-192">顯示下列其中一個狀態：[就緒] 或 [未就緒]。</span><span class="sxs-lookup"><span data-stu-id="02d06-192">Displays one of the following states: **Ready** or **Not ready**.</span></span>  
  
     <span data-ttu-id="02d06-193">**訊息**</span><span class="sxs-lookup"><span data-stu-id="02d06-193">**Message**</span></span>  
     <span data-ttu-id="02d06-194">**[訊息]** 資料行可以顯示有關資料庫的資訊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="02d06-194">The **Message** column may display information about the database, as follows:</span></span>  
  
    -   <span data-ttu-id="02d06-195">當資料庫涉及複寫時， **[狀態]** 為 **[尚未備妥]** 且 **[訊息]** 資料行會顯示 **[資料庫已複寫]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-195">When a database is involved with replication, the **Status** is **Not ready** and the **Message** column displays **Database replicated**.</span></span>  
  
    -   <span data-ttu-id="02d06-196">當資料庫有一或多個使用中的連線時，[狀態] 為 [未就緒] 且 [訊息] 資料行顯示 [<使用中連線數目> 個使用中的連線]，例如：[1 個使用中的連線]。</span><span class="sxs-lookup"><span data-stu-id="02d06-196">When a database has one or more active connections, the **Status** is **Not ready** and the **Message** column displays _<number_of_active_connections>_**Active connection(s)** - for example: **1 Active connection(s)**.</span></span> <span data-ttu-id="02d06-197">您必須選取 **[卸除連接]** 中斷任何使用中的連接之後，才能卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="02d06-197">Before you can detach the database, you need to disconnect any active connections by selecting **Drop Connections**.</span></span>  
  
     <span data-ttu-id="02d06-198">若要取得有關訊息的詳細資訊，請按一下超連結文字，以開啟活動監視器。</span><span class="sxs-lookup"><span data-stu-id="02d06-198">To obtain more information about a message, click the hyperlinked text to open Activity Monitor.</span></span>  
  
2.  <span data-ttu-id="02d06-199">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="02d06-199">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="02d06-200">使用 [Windows 檔案總管]，將資料庫檔案從來源伺服器移動或複製到目的地伺服器上相同的位置。</span><span class="sxs-lookup"><span data-stu-id="02d06-200">Using Windows Explorer, move or copy the database files from the source server to the same location on the destination server.</span></span>  
  
4.  <span data-ttu-id="02d06-201">使用 [Windows 檔案總管]，將伺服器憑證和私密金鑰檔案的備份從來源伺服器移動或複製到目的地伺服器上相同的位置。</span><span class="sxs-lookup"><span data-stu-id="02d06-201">Using Windows Explorer, move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.</span></span>  
  
5.  <span data-ttu-id="02d06-202">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的目的地執行個體上，建立資料庫主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="02d06-202">Create a database master key on the destination instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="02d06-203">如需詳細資訊，請參閱下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-203">For more information, see **Using Transact-SQL** below.</span></span>  
  
6.  <span data-ttu-id="02d06-204">使用原始伺服器憑證備份檔案重新建立伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="02d06-204">Recreate the server certificate by using the original server certificate backup file.</span></span> <span data-ttu-id="02d06-205">如需詳細資訊，請參閱下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-205">For more information, see **Using Transact-SQL** below.</span></span>  
  
7.  <span data-ttu-id="02d06-206">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 的 [物件總管] 中，以滑鼠右鍵按一下 [資料庫] 資料夾，然後選取 [附加...]。</span><span class="sxs-lookup"><span data-stu-id="02d06-206">In Object Explorer in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the **Databases** folder and select **Attach...**.</span></span>  
  
8.  <span data-ttu-id="02d06-207">在 **[附加資料庫]** 對話方塊中，按一下 **[要附加的資料庫]** 底下的 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-207">In the **Attach Databases** dialog box, under **Databases to attach**, click **Add**.</span></span>  
  
9. <span data-ttu-id="02d06-208">在 [**尋找資料庫檔案-**_server_name_ ] 對話方塊中，選取要附加至新伺服器的資料庫檔案，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="02d06-208">In the **Locate Database Files -**_server_name_ dialog box, select the database file to attach to the new server and click **OK**.</span></span>  
  
     <span data-ttu-id="02d06-209">**[附加資料庫]** 對話方塊有下列選項。</span><span class="sxs-lookup"><span data-stu-id="02d06-209">The following options are available in the **Attach Databases** dialog box.</span></span>  
  
     <span data-ttu-id="02d06-210">**[要附加的資料庫]**</span><span class="sxs-lookup"><span data-stu-id="02d06-210">**Databases to attach**</span></span>  
     <span data-ttu-id="02d06-211">顯示有關所選資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="02d06-211">Displays information about the selected databases.</span></span>  
  
     \<no column header>  
     <span data-ttu-id="02d06-212">顯示指出附加作業之狀態的圖示。</span><span class="sxs-lookup"><span data-stu-id="02d06-212">Displays an icon indicating the status of the attach operation.</span></span> <span data-ttu-id="02d06-213">可能的圖示將在以下的 **[狀態]** 描述中加以描述。</span><span class="sxs-lookup"><span data-stu-id="02d06-213">The possible icons are described in the **Status** description, below).</span></span>  
  
     <span data-ttu-id="02d06-214">**MDF 檔案位置**</span><span class="sxs-lookup"><span data-stu-id="02d06-214">**MDF File Location**</span></span>  
     <span data-ttu-id="02d06-215">顯示選取之 MDF 檔的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="02d06-215">Displays the path and file name of the selected MDF file.</span></span>  
  
     <span data-ttu-id="02d06-216">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="02d06-216">**Database Name**</span></span>  
     <span data-ttu-id="02d06-217">顯示資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="02d06-217">Displays the name of the database.</span></span>  
  
     <span data-ttu-id="02d06-218">**附加為**</span><span class="sxs-lookup"><span data-stu-id="02d06-218">**Attach As**</span></span>  
     <span data-ttu-id="02d06-219">選擇性地針對要附加的資料庫指定不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="02d06-219">Optionally, specifies a different name for the database to attach as.</span></span>  
  
     <span data-ttu-id="02d06-220">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="02d06-220">**Owner**</span></span>  
     <span data-ttu-id="02d06-221">提供包含可能的資料庫擁有者的下拉式清單，且您可以選擇性地從中選取不同的擁有者。</span><span class="sxs-lookup"><span data-stu-id="02d06-221">Provides a drop-down list of possible database owners from which you can optionally select a different owner.</span></span>  
  
     <span data-ttu-id="02d06-222">**狀態**</span><span class="sxs-lookup"><span data-stu-id="02d06-222">**Status**</span></span>  
     <span data-ttu-id="02d06-223">根據下表顯示資料庫的狀態。</span><span class="sxs-lookup"><span data-stu-id="02d06-223">Displays the status of the database according to the following table.</span></span>  
  
    |<span data-ttu-id="02d06-224">圖示</span><span class="sxs-lookup"><span data-stu-id="02d06-224">Icon</span></span>|<span data-ttu-id="02d06-225">狀態文字</span><span class="sxs-lookup"><span data-stu-id="02d06-225">Status text</span></span>|<span data-ttu-id="02d06-226">描述</span><span class="sxs-lookup"><span data-stu-id="02d06-226">Description</span></span>|  
    |----------|-----------------|-----------------|  
    |<span data-ttu-id="02d06-227">(無圖示)</span><span class="sxs-lookup"><span data-stu-id="02d06-227">(No icon)</span></span>|<span data-ttu-id="02d06-228">(沒有文字)</span><span class="sxs-lookup"><span data-stu-id="02d06-228">(No text)</span></span>|<span data-ttu-id="02d06-229">附加作業尚未啟動或是針對此物件進行暫止。</span><span class="sxs-lookup"><span data-stu-id="02d06-229">Attach operation has not been started or may be pending for this object.</span></span> <span data-ttu-id="02d06-230">當對話方塊開啟時，這是預設的動作。</span><span class="sxs-lookup"><span data-stu-id="02d06-230">This is the default when the dialog is opened.</span></span>|  
    |<span data-ttu-id="02d06-231">綠色、指向右方的三角形</span><span class="sxs-lookup"><span data-stu-id="02d06-231">Green, right-pointing triangle</span></span>|<span data-ttu-id="02d06-232">進行中</span><span class="sxs-lookup"><span data-stu-id="02d06-232">In progress</span></span>|<span data-ttu-id="02d06-233">附加作業已啟動，但尚未完成。</span><span class="sxs-lookup"><span data-stu-id="02d06-233">Attach operation has been started but it is not complete.</span></span>|  
    |<span data-ttu-id="02d06-234">綠色的核取記號</span><span class="sxs-lookup"><span data-stu-id="02d06-234">Green check mark</span></span>|<span data-ttu-id="02d06-235">Success</span><span class="sxs-lookup"><span data-stu-id="02d06-235">Success</span></span>|<span data-ttu-id="02d06-236">已順利附加物件。</span><span class="sxs-lookup"><span data-stu-id="02d06-236">The object has been attached successfully.</span></span>|  
    |<span data-ttu-id="02d06-237">包含白色十字的紅色圓圈</span><span class="sxs-lookup"><span data-stu-id="02d06-237">Red circle containing a white cross</span></span>|<span data-ttu-id="02d06-238">錯誤</span><span class="sxs-lookup"><span data-stu-id="02d06-238">Error</span></span>|<span data-ttu-id="02d06-239">附加作業發生錯誤，且未順利完成。</span><span class="sxs-lookup"><span data-stu-id="02d06-239">Attach operation encountered an error and did not complete successfully.</span></span>|  
    |<span data-ttu-id="02d06-240">包含兩個黑色的象限 (在左方和右方) 以及兩個白色的象限 (在上方和下方)</span><span class="sxs-lookup"><span data-stu-id="02d06-240">Circle containing two black quadrants (on left and right) and two white quadrants (on top and bottom)</span></span>|<span data-ttu-id="02d06-241">已停止</span><span class="sxs-lookup"><span data-stu-id="02d06-241">Stopped</span></span>|<span data-ttu-id="02d06-242">附加作業未順利完成，因為使用者已停止作業。</span><span class="sxs-lookup"><span data-stu-id="02d06-242">Attach operation was not completed successfully because the user stopped the operation.</span></span>|  
    |<span data-ttu-id="02d06-243">包含指向逆時針方向之彎曲箭頭的圓圈</span><span class="sxs-lookup"><span data-stu-id="02d06-243">Circle containing a curved arrow pointing counter-clockwise</span></span>|<span data-ttu-id="02d06-244">已回復</span><span class="sxs-lookup"><span data-stu-id="02d06-244">Rolled Back</span></span>|<span data-ttu-id="02d06-245">附加作業已順利完成，但是因為在附加其他物件的期間發生了錯誤，所以已將其回復。</span><span class="sxs-lookup"><span data-stu-id="02d06-245">Attach operation was successful but it has been rolled back due to an error during attachment of another object.</span></span>|  
  
     <span data-ttu-id="02d06-246">**訊息**</span><span class="sxs-lookup"><span data-stu-id="02d06-246">**Message**</span></span>  
     <span data-ttu-id="02d06-247">顯示空白訊息或「找不到檔案」超連結。</span><span class="sxs-lookup"><span data-stu-id="02d06-247">Displays either a blank message or a "File not found" hyperlink.</span></span>  
  
     <span data-ttu-id="02d06-248">**加入**</span><span class="sxs-lookup"><span data-stu-id="02d06-248">**Add**</span></span>  
     <span data-ttu-id="02d06-249">尋找需要的主要資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="02d06-249">Find the necessary main database files.</span></span> <span data-ttu-id="02d06-250">使用者選取 .mdf 檔案之後，適用的資訊會自動填入 **[要附加的資料庫]** 方格的對應欄位中。</span><span class="sxs-lookup"><span data-stu-id="02d06-250">When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="02d06-251">**移除**</span><span class="sxs-lookup"><span data-stu-id="02d06-251">**Remove**</span></span>  
     <span data-ttu-id="02d06-252">從 **[要附加的資料庫]** 方格中移除選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="02d06-252">Removes the selected file from the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="02d06-253">**"** _<database_name>_ **" database details**</span><span class="sxs-lookup"><span data-stu-id="02d06-253">**"** _<database_name>_ **" database details**</span></span>  
     <span data-ttu-id="02d06-254">顯示要附加之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="02d06-254">Displays the names of the files to be attached.</span></span> <span data-ttu-id="02d06-255">若要確認或變更檔案的路徑名稱，請按一下 [瀏覽] 按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="02d06-255">To verify or change the pathname of a file, click the **Browse** button (**...**).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="02d06-256">如果檔案不存在， **[訊息]** 資料行就會顯示「找不到」。</span><span class="sxs-lookup"><span data-stu-id="02d06-256">If a file does not exist, the **Message** column displays "Not found."</span></span> <span data-ttu-id="02d06-257">如果找不到記錄檔，它就存在於其他目錄中，或是已遭刪除。</span><span class="sxs-lookup"><span data-stu-id="02d06-257">If a log file is not found, it exists in another directory or has been deleted.</span></span> <span data-ttu-id="02d06-258">您必須更新 **[資料庫詳細資料]** 方格中的檔案路徑，以指向正確的位置，或是從方格中移除該記錄檔。</span><span class="sxs-lookup"><span data-stu-id="02d06-258">You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid.</span></span> <span data-ttu-id="02d06-259">如果找不到 .ndf 資料檔，您就必須更新該檔案在方格中的路徑，以指向正確的位置。</span><span class="sxs-lookup"><span data-stu-id="02d06-259">If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.</span></span>  
  
     <span data-ttu-id="02d06-260">**原始檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="02d06-260">**Original File Name**</span></span>  
     <span data-ttu-id="02d06-261">顯示屬於資料庫之附加檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="02d06-261">Displays the name of the attached file belonging to the database.</span></span>  
  
     <span data-ttu-id="02d06-262">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="02d06-262">**File Type**</span></span>  
     <span data-ttu-id="02d06-263">指出檔案的類型，即 **資料** 或 **記錄**。</span><span class="sxs-lookup"><span data-stu-id="02d06-263">Indicates the type of file, **Data** or **Log**.</span></span>  
  
     <span data-ttu-id="02d06-264">**目前的檔案路徑**</span><span class="sxs-lookup"><span data-stu-id="02d06-264">**Current File Path**</span></span>  
     <span data-ttu-id="02d06-265">顯示選取之資料庫檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="02d06-265">Displays the path to the selected database file.</span></span> <span data-ttu-id="02d06-266">路徑可以用手動的方式編輯。</span><span class="sxs-lookup"><span data-stu-id="02d06-266">The path can be edited manually.</span></span>  
  
     <span data-ttu-id="02d06-267">**訊息**</span><span class="sxs-lookup"><span data-stu-id="02d06-267">**Message**</span></span>  
     <span data-ttu-id="02d06-268">顯示空白訊息或 **「找不到檔案」** 超連結。</span><span class="sxs-lookup"><span data-stu-id="02d06-268">Displays either a blank message or a "**File not found**" hyperlink.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlMove"></a> <span data-ttu-id="02d06-269">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="02d06-269">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="02d06-270">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="02d06-270">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="02d06-271">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-271">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="02d06-272">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="02d06-272">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Detach the TDE protected database from the source server.   
    USE master ;  
    GO  
    EXEC master.dbo.sp_detach_db @dbname = N'CustRecords';  
    GO  
    -- Move or copy the database files from the source server to the same location on the destination server.   
    -- Move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.   
    -- Create a database master key on the destination instance of SQL Server.   
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    -- Recreate the server certificate by using the original server certificate backup file.   
    -- The password must be the same as the password that was used when the backup was created.  
  
    CREATE CERTIFICATE TestSQLServerCert   
    FROM FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        DECRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Attach the database that is being moved.   
    -- The path of the database files must be the location where you have stored the database files.  
    CREATE DATABASE [CustRecords] ON   
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords.mdf' ),  
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords_log.LDF' )  
    FOR ATTACH ;  
    GO  
    ```  
  
 <span data-ttu-id="02d06-273">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="02d06-273">For more information, see:</span></span>  
  
-   [<span data-ttu-id="02d06-274">sp_detach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-274">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [<span data-ttu-id="02d06-275">CREATE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-275">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="02d06-276">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-276">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="02d06-277">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-277">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="02d06-278">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02d06-278">See Also</span></span>  
 [<span data-ttu-id="02d06-279">資料庫卸離與附加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02d06-279">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../../databases/database-detach-and-attach-sql-server.md)  
  
  
