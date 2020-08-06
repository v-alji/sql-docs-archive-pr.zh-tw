---
title: 範例：使用憑證設定資料庫鏡像 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: df489ecd-deee-465c-a26a-6d1bef6d7b66
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea87e2de984107c5a0fda6eb2629ee5cfd197841
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709930"
---
# <a name="example-setting-up-database-mirroring-using-certificates-transact-sql"></a><span data-ttu-id="d54ff-102">範例：使用憑證設定資料庫鏡像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d54ff-102">Example: Setting Up Database Mirroring Using Certificates (Transact-SQL)</span></span>
  <span data-ttu-id="d54ff-103">此範例會顯示使用以憑證為基礎的驗證建立資料庫鏡像工作階段所需的所有階段。</span><span class="sxs-lookup"><span data-stu-id="d54ff-103">This example shows all the stages required to create a database mirroring session using certificate-based authentication.</span></span> <span data-ttu-id="d54ff-104">此主題中的範例使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d54ff-104">The examples in this topic use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d54ff-105">除非您可保證網路的安全無虞，否則建議您對資料庫鏡像連接使用加密。</span><span class="sxs-lookup"><span data-stu-id="d54ff-105">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span>  
  
 <span data-ttu-id="d54ff-106">將憑證複製到另一個系統時，請使用安全複製方法。</span><span class="sxs-lookup"><span data-stu-id="d54ff-106">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="d54ff-107">務必將您所有的憑證小心保管。</span><span class="sxs-lookup"><span data-stu-id="d54ff-107">Be extremely careful to keep all of your certificates secure.</span></span>  
  
##  <a name="example"></a><a name="ExampleH2"></a> <span data-ttu-id="d54ff-108">範例</span><span class="sxs-lookup"><span data-stu-id="d54ff-108">Example</span></span>  
 <span data-ttu-id="d54ff-109">下列範例示範必須針對位於 HOST_A 的一個夥伴完成什麼動作。</span><span class="sxs-lookup"><span data-stu-id="d54ff-109">The following example demonstrates what must be done on one partner that resides on HOST_A.</span></span> <span data-ttu-id="d54ff-110">此範例中的兩個夥伴都是三個電腦系統中的預設伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="d54ff-110">In this example, the two partners are the default server instances on three computer systems.</span></span> <span data-ttu-id="d54ff-111">兩個伺服器執行個體在不受信任的 Windows 網域上執行，因此必須有憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="d54ff-111">The two server instances run in nontrusted Windows domains, so certificate-based authentication is required.</span></span>  
  
 <span data-ttu-id="d54ff-112">由 HOST_A 取得初始主體角色，而由 HOST_B 取得鏡像角色。</span><span class="sxs-lookup"><span data-stu-id="d54ff-112">The initial principal role is taken by HOST_A, and the mirror role is taken by HOST_B.</span></span>  
  
 <span data-ttu-id="d54ff-113">使用憑證設定資料庫鏡像包含四個一般階段，其中三個階段 (1、2 和 4) 將由這則範例示範。</span><span class="sxs-lookup"><span data-stu-id="d54ff-113">Setting up database mirroring using certificates involves four general stages, of which three stages-1, 2, and 4-are demonstrated by this example.</span></span> <span data-ttu-id="d54ff-114">這些階段如下：</span><span class="sxs-lookup"><span data-stu-id="d54ff-114">These stages are as follows:</span></span>  
  
1.  [<span data-ttu-id="d54ff-115">設定傳出連接</span><span class="sxs-lookup"><span data-stu-id="d54ff-115">Configuring Outbound Connections</span></span>](#ConfiguringOutboundConnections)  
  
     <span data-ttu-id="d54ff-116">這個範例會說明下列作業的步驟：</span><span class="sxs-lookup"><span data-stu-id="d54ff-116">This example shows the steps for:</span></span>  
  
    1.  <span data-ttu-id="d54ff-117">設定傳出連接的 Host_A。</span><span class="sxs-lookup"><span data-stu-id="d54ff-117">Configuring Host_A for outbound connections.</span></span>  
  
    2.  <span data-ttu-id="d54ff-118">設定傳出連接的 Host_B。</span><span class="sxs-lookup"><span data-stu-id="d54ff-118">Configuring Host_B for outbound connections.</span></span>  
  
     <span data-ttu-id="d54ff-119">如需有關此設定資料庫鏡像階段的詳細資訊，請參閱 [允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-119">For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
2.  [<span data-ttu-id="d54ff-120">設定傳入連接</span><span class="sxs-lookup"><span data-stu-id="d54ff-120">Configuring Inbound Connections</span></span>](#ConfigureInboundConnections)  
  
     <span data-ttu-id="d54ff-121">這個範例會說明下列作業的步驟：</span><span class="sxs-lookup"><span data-stu-id="d54ff-121">This example shows the steps for:</span></span>  
  
    1.  <span data-ttu-id="d54ff-122">設定傳入連接的 Host_A。</span><span class="sxs-lookup"><span data-stu-id="d54ff-122">Configuring Host_A for inbound connections.</span></span>  
  
    2.  <span data-ttu-id="d54ff-123">設定傳入連接的 Host_B。</span><span class="sxs-lookup"><span data-stu-id="d54ff-123">Configuring Host_B for inbound connections.</span></span>  
  
     <span data-ttu-id="d54ff-124">如需有關此設定資料庫鏡像階段的詳細資訊，請參閱 [允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-124">For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
3.  <span data-ttu-id="d54ff-125">建立鏡像資料庫</span><span class="sxs-lookup"><span data-stu-id="d54ff-125">Creating the Mirror Database</span></span>  
  
     <span data-ttu-id="d54ff-126">如需有關如何建立鏡像資料庫的資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-126">For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
4.  [<span data-ttu-id="d54ff-127">設定鏡像夥伴</span><span class="sxs-lookup"><span data-stu-id="d54ff-127">Configuring the Mirroring Partners</span></span>](#ConfigureMirroringPartners)  
  
###  <a name="configuring-outbound-connections"></a><a name="ConfiguringOutboundConnections"></a> <span data-ttu-id="d54ff-128">設定傳出連接</span><span class="sxs-lookup"><span data-stu-id="d54ff-128">Configuring Outbound Connections</span></span>  
 <span data-ttu-id="d54ff-129">**若要設定傳出連接設定的 Host_A**</span><span class="sxs-lookup"><span data-stu-id="d54ff-129">**To configure Host_A for outbound connections**</span></span>  
  
1.  <span data-ttu-id="d54ff-130">在 master 資料庫上，若有需要，請建立資料庫主要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d54ff-130">On the master database, create the database master key, if needed.</span></span>  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
2.  <span data-ttu-id="d54ff-131">產生這個伺服器執行個體的憑證。</span><span class="sxs-lookup"><span data-stu-id="d54ff-131">Make a certificate for this server instance.</span></span>  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate';  
    GO  
    ```  
  
3.  <span data-ttu-id="d54ff-132">使用憑證建立伺服器執行個體的鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="d54ff-132">Create a mirroring endpoint for server instance using the certificate.</span></span>  
  
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
  
4.  <span data-ttu-id="d54ff-133">備份 HOST_A 憑證，並將它複製到其他系統 (HOST_B)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-133">Back up the HOST_A certificate, and copy it to other system, HOST_B.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
5.  <span data-ttu-id="d54ff-134">使用任何安全複製方法，將 C:\HOST_A_cert.cer 複製到 HOST_B。</span><span class="sxs-lookup"><span data-stu-id="d54ff-134">Using any secure copy method, copy C:\HOST_A_cert.cer to HOST_B.</span></span>  
  
 <span data-ttu-id="d54ff-135">**若要設定傳出連接設定的 Host_B**</span><span class="sxs-lookup"><span data-stu-id="d54ff-135">**To configure Host_B for outbound connections**</span></span>  
  
1.  <span data-ttu-id="d54ff-136">在 master 資料庫上，若有需要，請建立資料庫主要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d54ff-136">On the master database, create the database master key, if needed.</span></span>  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
    GO  
    ```  
  
2.  <span data-ttu-id="d54ff-137">在 HOST_B 伺服器執行個體上產生憑證。</span><span class="sxs-lookup"><span data-stu-id="d54ff-137">Make a certificate on the HOST_B server instance.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert   
       WITH SUBJECT = 'HOST_B certificate for database mirroring';  
    GO  
    ```  
  
3.  <span data-ttu-id="d54ff-138">在 HOST_B 上建立伺服器執行個體的鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="d54ff-138">Create a mirroring endpoint for the server instance on HOST_B.</span></span>  
  
    ```  
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
    ```  
  
4.  <span data-ttu-id="d54ff-139">備份 HOST_B 憑證。</span><span class="sxs-lookup"><span data-stu-id="d54ff-139">Back up HOST_B certificate.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
    GO   
    ```  
  
5.  <span data-ttu-id="d54ff-140">使用任何安全複製方法，將 C:\HOST_B_cert.cer 複製到 HOST_A。</span><span class="sxs-lookup"><span data-stu-id="d54ff-140">Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.</span></span>  
  
 <span data-ttu-id="d54ff-141">如需詳細資訊，請參閱 [允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-141">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
###  <a name="configuring-inbound-connections"></a><a name="ConfigureInboundConnections"></a> <span data-ttu-id="d54ff-142">設定傳入連接</span><span class="sxs-lookup"><span data-stu-id="d54ff-142">Configuring Inbound Connections</span></span>  
 <span data-ttu-id="d54ff-143">**若要設定傳入連接設定的 Host_A**</span><span class="sxs-lookup"><span data-stu-id="d54ff-143">**To configure Host_A for inbound connections**</span></span>  
  
1.  <span data-ttu-id="d54ff-144">在 HOST_A 上建立 HOST_B 的登入。</span><span class="sxs-lookup"><span data-stu-id="d54ff-144">Create a login on HOST_A for HOST_B.</span></span>  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_B_login WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
2.  <span data-ttu-id="d54ff-145">--為該登入建立使用者。</span><span class="sxs-lookup"><span data-stu-id="d54ff-145">--Create a user for that login.</span></span>  
  
    ```  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
3.  <span data-ttu-id="d54ff-146">--將憑證與使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d54ff-146">--Associate the certificate with the user.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
4.  <span data-ttu-id="d54ff-147">將 CONNECT 權限授與登入，以連接遠端鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="d54ff-147">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
 <span data-ttu-id="d54ff-148">**若要設定傳入連接設定的 Host_B**</span><span class="sxs-lookup"><span data-stu-id="d54ff-148">**To configure Host_B for inbound connections**</span></span>  
  
1.  <span data-ttu-id="d54ff-149">在 HOST_B 上建立 HOST_A 的登入。</span><span class="sxs-lookup"><span data-stu-id="d54ff-149">Create a login on HOST_B for HOST_A.</span></span>  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_A_login WITH PASSWORD = '=Sample#2_Strong_Password2';  
    GO  
    ```  
  
2.  <span data-ttu-id="d54ff-150">為該登入建立使用者。</span><span class="sxs-lookup"><span data-stu-id="d54ff-150">Create a user for that login.</span></span>  
  
    ```  
    CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
    GO  
    ```  
  
3.  <span data-ttu-id="d54ff-151">將憑證與使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d54ff-151">Associate the certificate with the user.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_A_cert  
       AUTHORIZATION HOST_A_user  
       FROM FILE = 'C:\HOST_A_cert.cer'  
    GO  
    ```  
  
4.  <span data-ttu-id="d54ff-152">將 CONNECT 權限授與登入，以連接遠端鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="d54ff-152">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_A_login];  
    GO  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d54ff-153">如果您想要在具有自動容錯移轉的高安全性模式下執行，就必須重複相同的設定步驟，以便設定傳出和傳入連接的見證。</span><span class="sxs-lookup"><span data-stu-id="d54ff-153">If you intend to run in high-safety mode with automatic failover, you must repeat the same setup steps to configure the witness for outbound and inbound connections.</span></span> <span data-ttu-id="d54ff-154">需要見證時若要設定傳入連接，您必須為兩個夥伴上的見證與見證上的兩個夥伴設定登入與使用者。</span><span class="sxs-lookup"><span data-stu-id="d54ff-154">Setting up the inbound connections when a witness is involved requires that you set up logins and users for the witness on both of the partners and for both partners on the witness.</span></span>  
  
 <span data-ttu-id="d54ff-155">如需詳細資訊，請參閱 [允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-155">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
### <a name="creating-the-mirror-database"></a><span data-ttu-id="d54ff-156">建立鏡像資料庫</span><span class="sxs-lookup"><span data-stu-id="d54ff-156">Creating the Mirror Database</span></span>  
 <span data-ttu-id="d54ff-157">如需有關如何建立鏡像資料庫的資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-157">For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
###  <a name="configuring-the-mirroring-partners"></a><a name="ConfigureMirroringPartners"></a> <span data-ttu-id="d54ff-158">設定鏡像夥伴</span><span class="sxs-lookup"><span data-stu-id="d54ff-158">Configuring the Mirroring Partners</span></span>  
  
1.  <span data-ttu-id="d54ff-159">在 HOST_B 的鏡像伺服器執行個體上，設定 HOST_A 上的伺服器執行個體為夥伴 (設定初始主體伺服器執行個體)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-159">On the mirror server instance on HOST_B, set the server instance on HOST_A as the partner (making it the initial principal server instance).</span></span> <span data-ttu-id="d54ff-160">以有效網路位址取代 `TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`。</span><span class="sxs-lookup"><span data-stu-id="d54ff-160">Substitute a valid network address for `TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`.</span></span> <span data-ttu-id="d54ff-161">如需詳細資訊，請參閱 [指定伺服器網路位址 &#40;資料庫鏡像&#41;](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-161">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
    ```  
    --At HOST_B, set server instance on HOST_A as partner (principal server):  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_A.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
2.  <span data-ttu-id="d54ff-162">在 HOST_A 的主體伺服器執行個體上，設定 HOST_B 上的伺服器執行個體為夥伴 (設定為初始鏡像伺服器執行個體)。</span><span class="sxs-lookup"><span data-stu-id="d54ff-162">On the principal server instance on HOST_A, set the server instance on HOST_B as the partner (making it the initial mirror server instance).</span></span> <span data-ttu-id="d54ff-163">以有效網路位址取代 `TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`。</span><span class="sxs-lookup"><span data-stu-id="d54ff-163">Substitute a valid network address for `TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`.</span></span>  
  
    ```  
    --At HOST_A, set server instance on HOST_B as partner (mirror server).  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
3.  <span data-ttu-id="d54ff-164">此範例假設工作階段將在高效能模式下執行。</span><span class="sxs-lookup"><span data-stu-id="d54ff-164">This example assumes that the session will be running in high-performance mode.</span></span> <span data-ttu-id="d54ff-165">若要設定此工作階段為高效能模式，請在主體伺服器執行個體上 (在 HOST_A 上) 設定交易安全性為 OFF。</span><span class="sxs-lookup"><span data-stu-id="d54ff-165">To configure this session for high-performance mode, on the principal server instance (on HOST_A), set transaction safety to OFF.</span></span>  
  
    ```  
    --Change to high-performance mode by turning off transacton safety.  
    ALTER DATABASE AdventureWorks   
        SET PARTNER SAFETY OFF  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="d54ff-166">如果您想要在具有自動容錯移轉的高安全性模式下執行，請保持交易安全性設定為 FULL (預設設定) 並在執行第二個 set PARTNER **' *`partner_server`* '** 語句後儘快新增見證。</span><span class="sxs-lookup"><span data-stu-id="d54ff-166">If you intend to run in high-safety mode with automatic failover, leave transaction safety set to FULL (the default setting) and add the witness as soon as possible after executing the second SET PARTNER **'*`partner_server`*'** statement.</span></span> <span data-ttu-id="d54ff-167">請注意，必須先為傳入與傳出設定見證。</span><span class="sxs-lookup"><span data-stu-id="d54ff-167">Note that the witness must first be configured for outbound and inbound connections.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d54ff-168">相關工作</span><span class="sxs-lookup"><span data-stu-id="d54ff-168">Related Tasks</span></span>  
  
-   [<span data-ttu-id="d54ff-169">準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d54ff-169">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="d54ff-170">允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d54ff-170">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="d54ff-171">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d54ff-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="d54ff-172">角色切換後針對登入和作業進行管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d54ff-172">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
-   <span data-ttu-id="d54ff-173">[在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d54ff-173">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) (SQL Server)</span></span>  
  
-   [<span data-ttu-id="d54ff-174">疑難排解資料庫鏡像組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d54ff-174">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="d54ff-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d54ff-175">See Also</span></span>  
 <span data-ttu-id="d54ff-176">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="d54ff-176">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="d54ff-177">[指定伺服器網路位址 &#40;資料庫鏡像&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="d54ff-177">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="d54ff-178">[資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d54ff-178">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="d54ff-179">[使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="d54ff-179">[Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) </span></span>  
 <span data-ttu-id="d54ff-180">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d54ff-180">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="d54ff-181">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="d54ff-181">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
