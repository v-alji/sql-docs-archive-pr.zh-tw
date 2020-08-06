---
title: 範例：使用 Windows 驗證設定資料庫鏡像 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- Windows authentication [SQL Server]
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: 35800769-aede-4aac-b077-0e0e487e302f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95df855e8e41c5937aae02884c71792537eb2bfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592199"
---
# <a name="example-setting-up-database-mirroring-using-windows-authentication-transact-sql"></a><span data-ttu-id="61ea7-102">範例：使用 Windows 驗證設定資料庫鏡像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61ea7-102">Example: Setting Up Database Mirroring Using Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="61ea7-103">此範例顯示使用 Windows 驗證建立具有見證的資料庫鏡像工作階段的所有必要階段。</span><span class="sxs-lookup"><span data-stu-id="61ea7-103">This example shows all the stages required to create a database mirroring session with a witness using Windows Authentication.</span></span> <span data-ttu-id="61ea7-104">此主題中的範例使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="61ea7-104">The examples in this topic use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="61ea7-105">請注意，使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 步驟的另一種方法是，您可以使用 [設定資料庫鏡像安全性精靈] 來設定資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="61ea7-105">Note that as an alternative to using [!INCLUDE[tsql](../../includes/tsql-md.md)] steps, you can use the Configure Database Mirroring Security Wizard for database mirroring setup.</span></span> <span data-ttu-id="61ea7-106">如需詳細資訊，請參閱本主題稍後的 [使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="61ea7-106">For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="61ea7-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="61ea7-107">Prerequisite</span></span>  
 <span data-ttu-id="61ea7-108">此範例使用 **AdventureWorks** 範例資料庫，依預設採用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="61ea7-108">The example uses the **AdventureWorks** sample database, which uses the simple recovery model by default.</span></span> <span data-ttu-id="61ea7-109">若要以此資料庫來使用資料庫鏡像，您必須改用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="61ea7-109">To use database mirroring with this database, you must alter it to use the full recovery model.</span></span> <span data-ttu-id="61ea7-110">若要在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中這樣做，請使用 ALTER DATABASE 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="61ea7-110">To do this in [!INCLUDE[tsql](../../includes/tsql-md.md)], use the ALTER DATABASE statement, as follows:</span></span>  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks   
SET RECOVERY FULL;  
GO  
```  
  
 <span data-ttu-id="61ea7-111">如需在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中變更復原模式的資訊，請參閱[檢視或變更資料庫的復原模式 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="61ea7-111">For information on changing the recovery model in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="61ea7-112">權限</span><span class="sxs-lookup"><span data-stu-id="61ea7-112">Permissions</span></span>  
 <span data-ttu-id="61ea7-113">需要資料庫的 ALTER 權限及 CREATE ENDPOINT 權限，或是 **sysadmin** 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="61ea7-113">Requires ALTER permission on the database and CREATE ENDPOINT permission, or membership in the **sysadmin** fixed server role.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61ea7-114">範例</span><span class="sxs-lookup"><span data-stu-id="61ea7-114">Example</span></span>  
 <span data-ttu-id="61ea7-115">此範例中的兩個夥伴伺服器和見證伺服器，各為三個電腦系統中的預設伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="61ea7-115">In this example, the two partners and the witness are the default server instances on three computer systems.</span></span> <span data-ttu-id="61ea7-116">這三個伺服器執行個體都執行相同的 Windows 網域，但範例之見證伺服器執行個體的使用者帳戶 (做為啟動服務帳戶使用) 與其他兩者不同。</span><span class="sxs-lookup"><span data-stu-id="61ea7-116">The three server instances run the same Windows domain, but the user account (used as the startup service account) is different for the example's witness server instance.</span></span>  
  
 <span data-ttu-id="61ea7-117">下表摘要說明此例中所使用的值。</span><span class="sxs-lookup"><span data-stu-id="61ea7-117">The following table summarizes the values used in this example.</span></span>  
  
|<span data-ttu-id="61ea7-118">初始鏡像角色</span><span class="sxs-lookup"><span data-stu-id="61ea7-118">Initial mirroring role</span></span>|<span data-ttu-id="61ea7-119">主機系統</span><span class="sxs-lookup"><span data-stu-id="61ea7-119">Host system</span></span>|<span data-ttu-id="61ea7-120">網域使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="61ea7-120">Domain user account</span></span>|  
|----------------------------|-----------------|-------------------------|  
|<span data-ttu-id="61ea7-121">主體</span><span class="sxs-lookup"><span data-stu-id="61ea7-121">Principal</span></span>|<span data-ttu-id="61ea7-122">PARTNERHOST1</span><span class="sxs-lookup"><span data-stu-id="61ea7-122">PARTNERHOST1</span></span>|<span data-ttu-id="61ea7-123">*\<Mydomain>\\<dbousername\>*</span><span class="sxs-lookup"><span data-stu-id="61ea7-123">*\<Mydomain>\\<dbousername\>*</span></span>|  
|<span data-ttu-id="61ea7-124">鏡像</span><span class="sxs-lookup"><span data-stu-id="61ea7-124">Mirror</span></span>|<span data-ttu-id="61ea7-125">PARTNERHOST5</span><span class="sxs-lookup"><span data-stu-id="61ea7-125">PARTNERHOST5</span></span>|<span data-ttu-id="61ea7-126">*\<Mydomain>\\<dbousername\>*</span><span class="sxs-lookup"><span data-stu-id="61ea7-126">*\<Mydomain>\\<dbousername\>*</span></span>|  
|<span data-ttu-id="61ea7-127">見證</span><span class="sxs-lookup"><span data-stu-id="61ea7-127">Witness</span></span>|<span data-ttu-id="61ea7-128">WITNESSHOST4</span><span class="sxs-lookup"><span data-stu-id="61ea7-128">WITNESSHOST4</span></span>|<span data-ttu-id="61ea7-129">*\<Somedomain>\\<witnessuser\>*</span><span class="sxs-lookup"><span data-stu-id="61ea7-129">*\<Somedomain>\\<witnessuser\>*</span></span>|  
  
1.  <span data-ttu-id="61ea7-130">在主體伺服器執行個體 (PARTNERHOST1 的預設執行個體) 上建立端點。</span><span class="sxs-lookup"><span data-stu-id="61ea7-130">Create an endpoint on the principal server instance (default instance on PARTNERHOST1).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=PARTNER)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    -- Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
2.  <span data-ttu-id="61ea7-131">在鏡像伺服器執行個體 (PARTNERHOST5 的預設執行個體) 上建立端點。</span><span class="sxs-lookup"><span data-stu-id="61ea7-131">Create an endpoint on the mirror server instance (default instance on PARTNERHOST5).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
3.  <span data-ttu-id="61ea7-132">在見證伺服器執行個體 (WITNESSHOST4 的預設執行個體) 上建立端點。</span><span class="sxs-lookup"><span data-stu-id="61ea7-132">Create an endpoint on the witness server instance (default instance on WITNESSHOST4).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    --Create a login for the partner server instances,  
    --which are both running as Mydomain\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [Mydomain\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
4.  <span data-ttu-id="61ea7-133">建立鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="61ea7-133">Create the mirror database.</span></span> <span data-ttu-id="61ea7-134">如需詳細資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="61ea7-134">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="61ea7-135">在 PARTNERHOST5 鏡像伺服器執行個體上，將 PARTNERHOST1 的伺服器執行個體設為夥伴伺服器 (也就是將其設為初始主體伺服器執行個體)。</span><span class="sxs-lookup"><span data-stu-id="61ea7-135">On the mirror server instance on PARTNERHOST5, set the server instance on PARTNERHOST1 as the partner (making it the initial principal server instance).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1.COM:7022'  
    GO  
    ```  
  
6.  <span data-ttu-id="61ea7-136">在 PARTNERHOST1 的主體伺服器執行個體上，將 PARTNERHOST5 的伺服器執行個體設為夥伴伺服器 (也就是將其設為初始鏡像伺服器執行個體)。</span><span class="sxs-lookup"><span data-stu-id="61ea7-136">On the principal server instance on PARTNERHOST1, set the server instance on PARTNERHOST5 as the partner (making it the initial mirror server instance).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5.COM:7022'  
    GO  
    ```  
  
7.  <span data-ttu-id="61ea7-137">在主體伺服器上，設定見證伺服器 (位於 WITNESSHOST4)。</span><span class="sxs-lookup"><span data-stu-id="61ea7-137">On the principal server, set the witness (which is on WITNESSHOST4).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4.COM:7022'  
    GO  
    ```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="61ea7-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="61ea7-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="61ea7-139">準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="61ea7-139">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="61ea7-140">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="61ea7-140">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
-   [<span data-ttu-id="61ea7-141">設定鏡像資料庫以使用 Trustworthy 屬性 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="61ea7-141">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
-   [<span data-ttu-id="61ea7-142">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="61ea7-142">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="61ea7-143">允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="61ea7-143">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="61ea7-144">範例：使用憑證設定資料庫鏡像 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="61ea7-144">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="61ea7-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61ea7-145">See Also</span></span>  
 <span data-ttu-id="61ea7-146">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="61ea7-146">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="61ea7-147">[資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="61ea7-147">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="61ea7-148">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="61ea7-148">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="61ea7-149">[在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="61ea7-149">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 [<span data-ttu-id="61ea7-150">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="61ea7-150">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
