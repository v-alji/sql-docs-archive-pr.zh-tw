---
title: 允許資料庫鏡像端點使用 (Transact-sql) 之輸出連接的憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- outbound connections [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 464c9096-10d6-4c5e-8bb1-19acba27ad9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f380f268f8d0f8d033db9c28f83d066d3f134571
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592216"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-outbound-connections-transact-sql"></a><span data-ttu-id="a7010-102">允許資料庫鏡像端點使用傳出連接的憑證 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a7010-102">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)</span></span>
  <span data-ttu-id="a7010-103">此主題描述設定伺服器執行個體的相關步驟，以便使用憑證來驗證資料庫鏡像的傳出連接。</span><span class="sxs-lookup"><span data-stu-id="a7010-103">This topic describes the steps for configuring server instances to use certificates to authenticate outbound connections for database mirroring.</span></span> <span data-ttu-id="a7010-104">您必須先完成傳出連接組態，才能設定傳入連接。</span><span class="sxs-lookup"><span data-stu-id="a7010-104">Outbound connection configuration must be done before you can set up inbound connections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7010-105">伺服器執行個體上的所有鏡像連接都使用單一資料庫鏡像端點，而您必須在建立端點時指定伺服器執行個體的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="a7010-105">All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.</span></span>  
  
 <span data-ttu-id="a7010-106">設定傳出連接的程序包含下列一般步驟：</span><span class="sxs-lookup"><span data-stu-id="a7010-106">The process of configuring outbound connections, involves the following general steps:</span></span>  
  
1.  <span data-ttu-id="a7010-107">在 **master** 資料庫中，建立資料庫「主要金鑰」。</span><span class="sxs-lookup"><span data-stu-id="a7010-107">In the **master** database, create a database Master Key.</span></span>  
  
2.  <span data-ttu-id="a7010-108">在 **master** 資料庫中，建立伺服器執行個體的加密憑證。</span><span class="sxs-lookup"><span data-stu-id="a7010-108">In the **master** database, create an encrypted certificate on the server instance.</span></span>  
  
3.  <span data-ttu-id="a7010-109">使用伺服器執行個體的憑證來建立其端點。</span><span class="sxs-lookup"><span data-stu-id="a7010-109">Create an endpoint for the server instance using its certificate.</span></span>  
  
4.  <span data-ttu-id="a7010-110">將憑證備份至檔案中，並以安全的方式將其複製到其他一或多個系統。</span><span class="sxs-lookup"><span data-stu-id="a7010-110">Back up the certificate to a file and securely copy it to the other system or systems.</span></span>  
  
 <span data-ttu-id="a7010-111">您必須為每一個夥伴或見證 (如果有的話) 完成上述步驟。</span><span class="sxs-lookup"><span data-stu-id="a7010-111">You must complete these steps for each partner and the witness, if there is one.</span></span>  
  
 <span data-ttu-id="a7010-112">下列程序將詳細說明這些步驟。</span><span class="sxs-lookup"><span data-stu-id="a7010-112">The following procedure describes these steps in detail.</span></span> <span data-ttu-id="a7010-113">對於每個步驟，此程序會提供在名為 HOST_A 的系統上設定伺服器執行個體的範例。</span><span class="sxs-lookup"><span data-stu-id="a7010-113">For each step, the procedure provides an example for configuring a server instance on a system named HOST_A.</span></span> <span data-ttu-id="a7010-114">隨附的「範例」部分則針對名為 HOST_B 系統上的另一個伺服器執行個體示範相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="a7010-114">The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a7010-115">程序</span><span class="sxs-lookup"><span data-stu-id="a7010-115">Procedure</span></span>  
  
#### <a name="to-configure-server-instances-for-outbound-mirroring-connections-on-host_a"></a><span data-ttu-id="a7010-116">設定 (HOST_A 上) 傳出鏡像連接的伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="a7010-116">To configure server instances for outbound mirroring connections (On HOST_A)</span></span>  
  
1.  <span data-ttu-id="a7010-117">在 **master** 資料庫中，若無資料庫「主要金鑰」存在，請加以建立。</span><span class="sxs-lookup"><span data-stu-id="a7010-117">On the **master** database, create the database Master Key, if none exists.</span></span> <span data-ttu-id="a7010-118">若要檢視資料庫的現有金鑰，請使用 [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="a7010-118">To view the existing keys for a database, use the [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) catalog view.</span></span>  
  
     <span data-ttu-id="a7010-119">若要建立資料庫「主要金鑰」，請使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="a7010-119">To create the database Master Key, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command:</span></span>  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
     <span data-ttu-id="a7010-120">使用唯一的增強式密碼，並將其記錄在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="a7010-120">Use a unique, strong password, and record it in a safe place.</span></span>  
  
     <span data-ttu-id="a7010-121">如需詳細資訊，請參閱 [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) 和[建立資料庫主要金鑰](../../relational-databases/security/encryption/create-a-database-master-key.md)。</span><span class="sxs-lookup"><span data-stu-id="a7010-121">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) and [Create a Database Master Key](../../relational-databases/security/encryption/create-a-database-master-key.md).</span></span>  
  
2.  <span data-ttu-id="a7010-122">在 **master** 資料庫中，建立伺服器執行個體的加密憑證，以供資料庫鏡像的傳出連接使用。</span><span class="sxs-lookup"><span data-stu-id="a7010-122">In the **master** database, create an encrypted certificate on the server instance to use for its outbound connections for database mirroring.</span></span>  
  
     <span data-ttu-id="a7010-123">例如，建立 HOST_A 系統的憑證。</span><span class="sxs-lookup"><span data-stu-id="a7010-123">For example, to create a certificate for the HOST_A system.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a7010-124">如果您想要使用此憑證一年以上，請在 CREATE CERTIFICATE 陳述式中使用 EXPIRY_DATE 選項來指定 UTC 時間格式的到期日。</span><span class="sxs-lookup"><span data-stu-id="a7010-124">If you intend to use the certificate for more than one year, specify the expiry date in UTC time by using the EXPIRY_DATE option in your CREATE CERTIFICATE statement.</span></span> <span data-ttu-id="a7010-125">此外，我們建議您使用 SQL Server Management Studio 建立原則式管理規則，在您的憑證即將過期時通知您。</span><span class="sxs-lookup"><span data-stu-id="a7010-125">Also, we recommend that you use SQL Server Management Studio to create a Policy-Based Management rule to alert you when your certificates are expiring.</span></span> <span data-ttu-id="a7010-126">使用原則管理的 **[建立新條件]** 對話方塊，在 **@ExpirationDate** Facet 的 **[@ExpirationDate]** 欄位上建立這個規則。</span><span class="sxs-lookup"><span data-stu-id="a7010-126">Using the Policy Management **Create New Condition** dialog box, create this rule on the **@ExpirationDate** field of the **Certificate** facet.</span></span> <span data-ttu-id="a7010-127">如需詳細資訊，請參閱 [使用原則式管理來管理伺服器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) 和 [保護 SQL Server 的安全](../../relational-databases/security/securing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a7010-127">For more information, see [Administer Servers by Using Policy-Based Management](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) and [Securing SQL Server](../../relational-databases/security/securing-sql-server.md).</span></span>  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate for database mirroring',   
       EXPIRY_DATE = '11/30/2013';  
    GO  
    ```  
  
     <span data-ttu-id="a7010-128">如需詳細資訊，請參閱 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a7010-128">For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="a7010-129">若要檢視 **master** 資料庫中的憑證，您可以使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a7010-129">To view the certificates in the **master** database, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    SELECT * FROM sys.certificates;  
    ```  
  
     <span data-ttu-id="a7010-130">如需詳細資訊，請參閱 [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a7010-130">For more information, see [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).</span></span>  
  
3.  <span data-ttu-id="a7010-131">確定每個伺服器執行個體上都有資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="a7010-131">Ensure that the database mirroring endpoint exist on each of the server instances.</span></span>  
  
     <span data-ttu-id="a7010-132">若伺服器執行個體上已有資料庫鏡像端點，您應在伺服器執行個體上所建立的任何其他工作階段，重複使用該端點。</span><span class="sxs-lookup"><span data-stu-id="a7010-132">If a database mirroring endpoint already exists for the server instance, you should reuse that endpoint for any other sessions you establish on the server instance.</span></span> <span data-ttu-id="a7010-133">若要判斷伺服器執行個體上是否有資料庫鏡像端點，以及檢視該端點的組態，請使用下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="a7010-133">To determine whether a database mirroring endpoint exists on a server instance and to view its configuration, use the following statement:</span></span>  
  
    ```  
    SELECT name, role_desc, state_desc, connection_auth_desc, encryption_algorithm_desc   
       FROM sys.database_mirroring_endpoints;  
    ```  
  
     <span data-ttu-id="a7010-134">若沒有端點存在，請建立一個端點，並使其在傳出連接上使用此憑證，而對其他系統的驗證則使用憑證的認證。</span><span class="sxs-lookup"><span data-stu-id="a7010-134">If no endpoint exists, create an endpoint that uses this certificate for outbound connections and that uses the certificate's credentials for verification on the other system.</span></span> <span data-ttu-id="a7010-135">這屬於伺服器範圍的端點，可供伺服器執行個體參與的所有鏡像工作階段使用。</span><span class="sxs-lookup"><span data-stu-id="a7010-135">This is a server-wide endpoint that is used by all mirroring sessions in which the server instance participates.</span></span>  
  
     <span data-ttu-id="a7010-136">例如，為 HOST_A 上的範例伺服器執行個體建立鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="a7010-136">For example, to create a mirroring endpoint for the example server instance on HOST_A.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_A_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
     <span data-ttu-id="a7010-137">如需詳細資訊，請參閱 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a7010-137">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
4.  <span data-ttu-id="a7010-138">備份憑證，並將其複製到其他一或多個系統。</span><span class="sxs-lookup"><span data-stu-id="a7010-138">Back up the certificate and copy it to the other system or systems.</span></span> <span data-ttu-id="a7010-139">若要在其他系統上設定傳入連接，就必須執行此動作。</span><span class="sxs-lookup"><span data-stu-id="a7010-139">This is necessary in order to configure inbound connections on the other system.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
     <span data-ttu-id="a7010-140">如需詳細資訊，請參閱 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a7010-140">For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="a7010-141">使用您所選的任何安全方式來複製此憑證。</span><span class="sxs-lookup"><span data-stu-id="a7010-141">Copy this certificate using any secure method you choose.</span></span> <span data-ttu-id="a7010-142">務必將您所有的憑證小心保管。</span><span class="sxs-lookup"><span data-stu-id="a7010-142">Be extremely careful to keep all of your certificates secure.</span></span>  
  
 <span data-ttu-id="a7010-143">前述幾個步驟中的範例程式碼會設定 HOST_A 上的傳出連接。</span><span class="sxs-lookup"><span data-stu-id="a7010-143">The example code in the preceding steps configure outbound connections on HOST_A.</span></span>  
  
 <span data-ttu-id="a7010-144">接著，您必須為 HOST_B 執行對等的傳出步驟。</span><span class="sxs-lookup"><span data-stu-id="a7010-144">You now need to perform the equivalent outbound steps for HOST_B.</span></span> <span data-ttu-id="a7010-145">這些步驟將在下一節＜範例＞中說明。</span><span class="sxs-lookup"><span data-stu-id="a7010-145">These steps are illustrated in the following Example section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7010-146">範例</span><span class="sxs-lookup"><span data-stu-id="a7010-146">Example</span></span>  
 <span data-ttu-id="a7010-147">下列範例示範如何針對傳出連接設定 HOST_B。</span><span class="sxs-lookup"><span data-stu-id="a7010-147">The following example demonstrates configuring HOST_B for outbound connections.</span></span>  
  
```  
USE master;  
--Create the database Master Key, if needed.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
GO  
-- Make a certifcate on HOST_B server instance.  
CREATE CERTIFICATE HOST_B_cert   
   WITH SUBJECT = 'HOST_B certificate for database mirroring',   
   EXPIRY_DATE = '11/30/2013';  
GO  
--Create a mirroring endpoint for the server instance on HOST_B.  
CREATE ENDPOINT Endpoint_Mirroring  
   STATE = STARTED  
   AS TCP (  
      LISTENER_PORT=7024  
      , LISTENER_IP = ALL  
   )   
   FOR DATABASE_MIRRORING (   
      AUTHENTICATION = CERTIFICATE HOST_B_cert  
      , ENCRYPTION = REQUIRED ALGORITHM AES  
      , ROLE = ALL  
   );  
GO  
--Backup HOST_B certificate.  
BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
GO   
--Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.  
```  
  
 <span data-ttu-id="a7010-148">使用您所選的任何安全方式，將憑證複製到其他系統。</span><span class="sxs-lookup"><span data-stu-id="a7010-148">Copy the certificate to the other system using any secure method you choose.</span></span> <span data-ttu-id="a7010-149">務必將您所有的憑證小心保管。</span><span class="sxs-lookup"><span data-stu-id="a7010-149">Be extremely careful to keep all of your certificates secure.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a7010-150">在設定傳出連接後，您必須在每個伺服器執行個體上設定其他一或多個伺服器執行個體的傳入連接。</span><span class="sxs-lookup"><span data-stu-id="a7010-150">After you set up outbound connections, you must configure inbound connections on each server instance for the other server instance or instances.</span></span> <span data-ttu-id="a7010-151">如需詳細資訊，請參閱 [允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="a7010-151">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
 <span data-ttu-id="a7010-152">如需建立鏡像資料庫的相關資訊，包括 Transact-SQL 範例在內，請參閱[準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a7010-152">For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="a7010-153">如需建立高效能模式工作階段的 Transact-SQL 範例，請參閱[範例：使用憑證設定資料庫鏡像 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="a7010-153">For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a7010-154">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="a7010-154">.NET Framework Security</span></span>  
 <span data-ttu-id="a7010-155">除非您可保證網路的安全無虞，否則建議您對資料庫鏡像連接使用加密。</span><span class="sxs-lookup"><span data-stu-id="a7010-155">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span>  
  
 <span data-ttu-id="a7010-156">將憑證複製到另一個系統時，請使用安全複製方法。</span><span class="sxs-lookup"><span data-stu-id="a7010-156">When copying a certificate to another system, use a secure copy method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7010-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7010-157">See Also</span></span>  
 <span data-ttu-id="a7010-158">[選擇加密演算法](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a7010-158">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="a7010-159">[準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a7010-159">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="a7010-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7010-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="a7010-161">[範例：使用憑證設定資料庫鏡像 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="a7010-161">[Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md) </span></span>  
 <span data-ttu-id="a7010-162">[資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a7010-162">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="a7010-163">[為資料庫鏡像組態進行疑難排解 &#40;SQL Server&#41; &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a7010-163">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="a7010-164">設定加密鏡像資料庫</span><span class="sxs-lookup"><span data-stu-id="a7010-164">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
  
