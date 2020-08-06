---
title: 允許資料庫鏡像端點使用 (Transact-sql) 的輸入連接憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- inbound connections
- database mirroring [SQL Server], security
ms.assetid: 5d48bb98-61f0-4b99-8f1a-b53f831d63d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c05397dfbd1740293c4b154ace1ed5704cec11a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592217"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-inbound-connections-transact-sql"></a><span data-ttu-id="7fbb0-102">允許資料庫鏡像端點使用傳入連接的憑證 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7fbb0-102">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)</span></span>
  <span data-ttu-id="7fbb0-103">此主題描述設定伺服器執行個體，以使用憑證來驗證資料庫鏡像之傳入連接的步驟。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-103">This topic describes the steps for configuring server instances to use certificates to authenticate inbound connections for database mirroring.</span></span> <span data-ttu-id="7fbb0-104">在設定傳入連接之前，您必須先在每一個伺服器執行個體上設定傳出連接。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-104">Before you can set up inbound connections, you must configure outbound connections on each server instance.</span></span> <span data-ttu-id="7fbb0-105">如需詳細資訊，請參閱 [允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-105">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
 <span data-ttu-id="7fbb0-106">設定傳入連接的程序，包括下列一般步驟：</span><span class="sxs-lookup"><span data-stu-id="7fbb0-106">The process of configuring inbound connections, involves the following general steps:</span></span>  
  
1.  <span data-ttu-id="7fbb0-107">為其他系統建立登入。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-107">Create a login for other system.</span></span>  
  
2.  <span data-ttu-id="7fbb0-108">為該登入建立使用者。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-108">Create a user for that login.</span></span>  
  
3.  <span data-ttu-id="7fbb0-109">取得另一個伺服器執行個體的鏡像端點的憑證。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-109">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
4.  <span data-ttu-id="7fbb0-110">使憑證與步驟 2 所建立的使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-110">Associate the certificate with the user created in step 2.</span></span>  
  
5.  <span data-ttu-id="7fbb0-111">將 CONNECT 權限授與登入，以連接該鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-111">Grant CONNECT permission on the login for that mirroring endpoint.</span></span>  
  
 <span data-ttu-id="7fbb0-112">如果有見證，您也必須為它設定傳入連接。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-112">If there is a witness, you must also set up inbound connections for it.</span></span> <span data-ttu-id="7fbb0-113">這需要在兩個夥伴上設定見證的登入、使用者和憑證，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-113">This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.</span></span>  
  
 <span data-ttu-id="7fbb0-114">下列程序將詳細說明這些步驟。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-114">The following procedure describes these steps in detail.</span></span> <span data-ttu-id="7fbb0-115">對於每個步驟，此程序會提供在名為 HOST_A 的系統上設定伺服器執行個體的範例。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-115">For each step, the procedure provides an example for configuring a server instance on a system named HOST_A.</span></span> <span data-ttu-id="7fbb0-116">隨附的「範例」部分則針對名為 HOST_B 系統上的另一個伺服器執行個體示範相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-116">The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.</span></span>  
  
### <a name="to-configure-server-instances-for-inbound-mirroring-connections-on-host_a"></a><span data-ttu-id="7fbb0-117">設定 (HOST_A 上) 傳入鏡像連接的伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="7fbb0-117">To configure server instances for inbound mirroring connections (on HOST_A)</span></span>  
  
1.  <span data-ttu-id="7fbb0-118">為其他系統建立登入。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-118">Create a login for the other system.</span></span>  
  
     <span data-ttu-id="7fbb0-119">下列範例在 HOST_A 之伺服器執行個體的 **master** 資料庫中，建立系統 HOST_B 的登入；在此範例中，登入名稱為 `HOST_B_login`。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-119">The following example creates a login for the system, HOST_B, in the **master** database of the server instance on HOST_A; in this example, the login is named `HOST_B_login`.</span></span> <span data-ttu-id="7fbb0-120">以您自己的密碼取代範例密碼。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-120">Substitute a password of your own for the sample password.</span></span>  
  
    ```sql  
    USE master;  
    CREATE LOGIN HOST_B_login   
       WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
     <span data-ttu-id="7fbb0-121">如需詳細資訊，請參閱 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-121">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
     <span data-ttu-id="7fbb0-122">若要檢視此伺服器執行個體上的登入，您可以使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7fbb0-122">To view the logins on this server instance, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.server_principals;  
    ```  
  
     <span data-ttu-id="7fbb0-123">如需詳細資訊，請參閱 [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-123">For more information, see [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql).</span></span>  
  
2.  <span data-ttu-id="7fbb0-124">為該登入建立使用者。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-124">Create a user for that login.</span></span>  
  
     <span data-ttu-id="7fbb0-125">下列範例為上一個步驟所建立的登入，建立使用者 `HOST_B_user`。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-125">The following example creates a user, `HOST_B_user`, for the login created in the preceding step.</span></span>  
  
    ```sql  
    USE master;  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
     <span data-ttu-id="7fbb0-126">如需詳細資訊，請參閱 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-126">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
     <span data-ttu-id="7fbb0-127">若要檢視此伺服器執行個體上的使用者，您可以使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7fbb0-127">To view the users on this server instance, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.sysusers;  
    ```  
  
     <span data-ttu-id="7fbb0-128">如需詳細資訊，請參閱 [sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-128">For more information, see [sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql).</span></span>  
  
3.  <span data-ttu-id="7fbb0-129">取得另一個伺服器執行個體的鏡像端點的憑證。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-129">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
     <span data-ttu-id="7fbb0-130">如果在設定傳出連接前，您尚未這麼做，請為遠端伺服器執行個體的鏡像端點取得憑證副本。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-130">If you have not already done so when configuring outbound connections, obtain a copy of the certificate for the mirroring endpoint of the remote server instance.</span></span> <span data-ttu-id="7fbb0-131">若要這樣做，請依[允許資料庫鏡像端點使用傳出連接的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)中所述在該伺服器執行個體上備份憑證。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-131">To do this, back up the certificate on that server instance as described in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span> <span data-ttu-id="7fbb0-132">將憑證複製到另一個系統時，請使用安全複製方法。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-132">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="7fbb0-133">務必將您所有的憑證小心保管。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-133">Be extremely careful to keep all of your certificates secure.</span></span>  
  
     <span data-ttu-id="7fbb0-134">如需詳細資訊，請參閱 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-134">For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).</span></span>  
  
4.  <span data-ttu-id="7fbb0-135">使憑證與步驟 2 所建立的使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-135">Associate the certificate with the user created in step 2.</span></span>  
  
     <span data-ttu-id="7fbb0-136">下列範例使 HOST_B 的憑證與它在 HOST_A 的使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-136">The following example, associates the certificate of HOST_B with its user on HOST_A.</span></span>  
  
    ```sql  
    USE master;  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
     <span data-ttu-id="7fbb0-137">如需詳細資訊，請參閱 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-137">For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="7fbb0-138">若要檢視此伺服器執行個體上的憑證，請使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7fbb0-138">To view the certificates on this server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.certificates;  
    ```  
  
     <span data-ttu-id="7fbb0-139">如需詳細資訊，請參閱 [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-139">For more information, see [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).</span></span>  
  
5.  <span data-ttu-id="7fbb0-140">將 CONNECT 權限授與登入，以連接遠端鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-140">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
     <span data-ttu-id="7fbb0-141">例如，若要在 HOST_A 上授與權限給 HOST_B 上的遠端伺服器執行個體來連接到其本機登入 (也就是連接到 `HOST_B_login`)，請使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7fbb0-141">For example, to grant permission on HOST_A to the remote server instance on HOST_B to connect to its local login-that is, to connect to `HOST_B_login`-use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```sql  
    USE master;  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
     <span data-ttu-id="7fbb0-142">如需詳細資訊，請參閱 [GRANT 端點權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-142">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
 <span data-ttu-id="7fbb0-143">如此即完成為 HOST_B 設定憑證驗證來登入到 HOST_A。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-143">This completes setting up certificate authentication for HOST_B to log in to HOST_A.</span></span>  
  
 <span data-ttu-id="7fbb0-144">接著，您必須為 HOST_B 上的 HOST_A 執行對等的傳入步驟。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-144">You now need to perform the equivalent inbound steps for HOST_A on HOST_B.</span></span> <span data-ttu-id="7fbb0-145">這些步驟將在下一節＜範例＞中範例的傳入部分加以說明。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-145">These steps are illustrated in the inbound portion of the example in the Example section, below.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fbb0-146">範例</span><span class="sxs-lookup"><span data-stu-id="7fbb0-146">Example</span></span>  
 <span data-ttu-id="7fbb0-147">下列範例示範設定 HOST_B 的傳入連接。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-147">The following example demonstrates configuring HOST_B for inbound connections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7fbb0-148">本例使用包含 HOST_A 憑證的憑證檔案，此 HOST_A 憑證是由[允許資料庫鏡像端點使用傳出連接的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md) 中的程式碼片段所建立。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-148">This example uses a certificate file containing the HOST_A certificate that is created by a code snippet in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
```sql  
USE master;  
--On HOST_B, create a login for HOST_A.  
CREATE LOGIN HOST_A_login WITH PASSWORD = 'AStrongPassword!@#';  
GO  
--Create a user, HOST_A_user, for that login.  
CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
GO  
--Obtain HOST_A certificate. (See the note   
--   preceding this example.)  
--Asscociate this certificate with the user, HOST_A_user.  
CREATE CERTIFICATE HOST_A_cert  
   AUTHORIZATION HOST_A_user  
   FROM FILE = 'C:\HOST_A_cert.cer';  
GO  
--Grant CONNECT permission for the server instance on HOST_A.  
GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO HOST_A_login;  
GO  
```  
  
 <span data-ttu-id="7fbb0-149">如果您想要在具有自動容錯移轉的高安全性模式下執行，就必須重複相同的設定步驟，以便設定傳出和傳入連接的見證。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-149">If you intend to run in high-safety mode with automatic failover, you must repeat the same set up steps to configure the witness for outbound and inbound connections.</span></span>  
  
 <span data-ttu-id="7fbb0-150">如需建立鏡像資料庫的相關資訊，包括 Transact-SQL 範例在內，請參閱[準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-150">For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="7fbb0-151">如需建立高效能模式工作階段的 Transact-SQL 範例，請參閱[範例：使用憑證設定資料庫鏡像 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-151">For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7fbb0-152">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="7fbb0-152">.NET Framework Security</span></span>  
 <span data-ttu-id="7fbb0-153">將憑證複製到另一個系統時，請使用安全複製方法。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-153">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="7fbb0-154">務必將您所有的憑證小心保管。</span><span class="sxs-lookup"><span data-stu-id="7fbb0-154">Be extremely careful to keep all of your certificates secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fbb0-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fbb0-155">See Also</span></span>  
 <span data-ttu-id="7fbb0-156">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="7fbb0-156">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="7fbb0-157">[GRANT 端點權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7fbb0-157">[GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span></span>  
 <span data-ttu-id="7fbb0-158">[設定加密鏡像資料庫](set-up-an-encrypted-mirror-database.md) </span><span class="sxs-lookup"><span data-stu-id="7fbb0-158">[Set Up an Encrypted Mirror Database](set-up-an-encrypted-mirror-database.md) </span></span>  
 <span data-ttu-id="7fbb0-159">[資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7fbb0-159">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 [<span data-ttu-id="7fbb0-160">疑難排解資料庫鏡像組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7fbb0-160">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
