---
title: 設定 AlwaysOn 可用性群組的複寫 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 4e001426-5ae0-4876-85ef-088d6e3fb61c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 916458d2d6b8fbba81940257ee85ffe014d1f12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688233"
---
# <a name="configure-replication-for-always-on-availability-groups-sql-server"></a><span data-ttu-id="41afb-102">設定 AlwaysOn 可用性群組的複寫 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="41afb-102">Configure Replication for Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="41afb-103">設定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫和 AlwaysOn 可用性群組包含七個步驟。</span><span class="sxs-lookup"><span data-stu-id="41afb-103">Configuring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication and AlwaysOn availability groups involves seven steps.</span></span> <span data-ttu-id="41afb-104">下列各節將詳細說明每個步驟。</span><span class="sxs-lookup"><span data-stu-id="41afb-104">Each step is described in more detail in the following sections.</span></span>  

##  <a name="1-configure-the-database-publications-and-subscriptions"></a><a name="step1"></a> <span data-ttu-id="41afb-105">1.設定資料庫發行集和訂閱</span><span class="sxs-lookup"><span data-stu-id="41afb-105">1. Configure the Database Publications and Subscriptions</span></span>  

### <a name="configure-the-distributor"></a><span data-ttu-id="41afb-106">設定散發者</span><span class="sxs-lookup"><span data-stu-id="41afb-106">Configure the distributor</span></span>
  
 <span data-ttu-id="41afb-107">散發者不應該是發行資料庫屬於 (或即將成為) 其成員之可用性群組任何目前 (或預期) 複本的主機。</span><span class="sxs-lookup"><span data-stu-id="41afb-107">The distributor should not be a host for any of the current (or intended) replicas of the availability group that the publishing database is (or will become) a member of.</span></span>  
  
1.  <span data-ttu-id="41afb-108">在散發者端設定散發。</span><span class="sxs-lookup"><span data-stu-id="41afb-108">Configure distribution at the distributor.</span></span> <span data-ttu-id="41afb-109">如果預存程序正用於組態設定，請執行 `sp_adddistributor`。</span><span class="sxs-lookup"><span data-stu-id="41afb-109">If stored procedures are being used for configuration, run `sp_adddistributor`.</span></span> <span data-ttu-id="41afb-110">使用 *@password* 參數來識別遠端發行者連接到散發者時將使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="41afb-110">Use the *@password* parameter to identify the password that will be used when a remote publisher connects to the distributor.</span></span> <span data-ttu-id="41afb-111">設定遠端散發者時，每個遠端發行者也需要此密碼。</span><span class="sxs-lookup"><span data-stu-id="41afb-111">The password will also be needed at each remote publisher when the remote distributor is set up.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = '**Strong password for distributor**';  
    ```  
  
2.  <span data-ttu-id="41afb-112">在散發者端建立散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="41afb-112">Create the distribution database at the distributor.</span></span> <span data-ttu-id="41afb-113">如果預存程序正用於組態設定，請執行 `sp_adddistributiondb`。</span><span class="sxs-lookup"><span data-stu-id="41afb-113">If stored procedures are being used for configuration, run `sp_adddistributiondb`.</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributiondb  
        @database = 'distribution',  
        @security_mode = 1;  
    ```  
  
3.  <span data-ttu-id="41afb-114">設定遠端發行者。</span><span class="sxs-lookup"><span data-stu-id="41afb-114">Configure the remote publisher.</span></span> <span data-ttu-id="41afb-115">如果預存程序正用於設定散發者，請執行 `sp_adddistpublisher`。</span><span class="sxs-lookup"><span data-stu-id="41afb-115">If stored procedures are being used to configure the distributor, run `sp_adddistpublisher`.</span></span> <span data-ttu-id="41afb-116">*@security_mode*參數是用來決定從複寫代理程式執行的發行者驗證預存程式如何連接到目前的主要複本。</span><span class="sxs-lookup"><span data-stu-id="41afb-116">The *@security_mode* parameter is used to determine how the publisher validation stored procedure that is run from the replication agents, connects to the current primary.</span></span> <span data-ttu-id="41afb-117">如果設定為 1，就會使用 Windows 驗證來連接到目前主要複本。</span><span class="sxs-lookup"><span data-stu-id="41afb-117">If set to 1 Windows authentication is used to connect to the current primary.</span></span> <span data-ttu-id="41afb-118">如果設定為0， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 則會使用驗證搭配指定的 *@login* 和 *@password* 值。</span><span class="sxs-lookup"><span data-stu-id="41afb-118">If set to 0, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authentication is used with the specified *@login* and *@password* values.</span></span> <span data-ttu-id="41afb-119">在每個次要複本上指定的登入和密碼必須有效，才能讓驗證預存程序成功連接到該複本。</span><span class="sxs-lookup"><span data-stu-id="41afb-119">The login and password specified must be valid at each secondary replica for the validation stored procedure to successfully connect to that replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="41afb-120">如果任何修改的複寫代理程式在散發者以外的電腦上執行，則使用 Windows 驗證來連接到主要複本時，就必須針對複本主機電腦之間的通訊設定 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="41afb-120">If any modified replication agents run on a computer other than the distributor, use of Windows authentication for the connection to the primary will require Kerberos authentication to be configured for the communication between the replica host computers.</span></span> <span data-ttu-id="41afb-121">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入來連接到目前主要複本時，不需要 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="41afb-121">Use of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login for the connection to the current primary will not require Kerberos authentication.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistpublisher  
        @publisher = 'AGPrimaryReplicaHost',  
        @distribution_db = 'distribution',  
        @working_directory = '\\MyReplShare\WorkingDir',  
        @login = 'MyPubLogin',  
        @password = '**Strong password for publisher**';  
    ```  
  
 <span data-ttu-id="41afb-122">如需詳細資訊，請參閱 [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="41afb-122">For more information, see [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql).</span></span>  
  
### <a name="configure-the-publisher-at-the-original-publisher"></a><span data-ttu-id="41afb-123">在原始發行者端設定發行者</span><span class="sxs-lookup"><span data-stu-id="41afb-123">Configure the publisher at the original publisher</span></span>
  
1.  <span data-ttu-id="41afb-124">設定遠端散發。</span><span class="sxs-lookup"><span data-stu-id="41afb-124">Configure remote distribution.</span></span> <span data-ttu-id="41afb-125">如果預存程序正用於設定發行者，請執行 `sp_adddistributor`。</span><span class="sxs-lookup"><span data-stu-id="41afb-125">If stored procedures are being used to configure the publisher, run `sp_adddistributor`.</span></span> <span data-ttu-id="41afb-126">指定與在散發者端 *@password* 執行時所使用的相同值， `sp_adddistrbutor` 以設定散發。</span><span class="sxs-lookup"><span data-stu-id="41afb-126">Specify the same value for *@password* as that used when `sp_adddistrbutor` was run at the distributor to set up distribution.</span></span>  
  
    ```sql
    exec sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = 'MyDistPass'  
    ```  
  
2.  <span data-ttu-id="41afb-127">啟用資料庫進行複寫。</span><span class="sxs-lookup"><span data-stu-id="41afb-127">Enable the database for replication.</span></span> <span data-ttu-id="41afb-128">如果預存程序正用於設定發行者，請執行 `sp_replicationdboption`。</span><span class="sxs-lookup"><span data-stu-id="41afb-128">If stored procedures are being used to configure the publisher, run `sp_replicationdboption`.</span></span> <span data-ttu-id="41afb-129">如果要針對資料庫設定異動和合併式複寫，就必須啟用每個複寫。</span><span class="sxs-lookup"><span data-stu-id="41afb-129">If both transactional and merge replication are to be configured for the database, each must be enabled.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'true';  
  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'merge publish',  
        @value = 'true';  
    ```  
  
3.  <span data-ttu-id="41afb-130">建立複寫發行集、發行項和訂閱。</span><span class="sxs-lookup"><span data-stu-id="41afb-130">Create the replication publication, articles, and subscriptions.</span></span> <span data-ttu-id="41afb-131">如需有關如何設定複寫的詳細資訊，請參閱＜發行資料和資料庫物件＞。</span><span class="sxs-lookup"><span data-stu-id="41afb-131">For more information about how to configure replication, see Publishing Data and Database objects.</span></span>  
  
##  <a name="2-configure-the-alwayson-availability-group"></a><a name="step2"></a><span data-ttu-id="41afb-132">2. 設定 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="41afb-132">2. Configure the AlwaysOn Availability Group</span></span>  
 <span data-ttu-id="41afb-133">在預期的主要複本上，建立具有已發行 (或即將發行) 資料庫做為成員資料庫的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="41afb-133">At the intended primary, create the availability group with the published (or to be published) database as a member database.</span></span> <span data-ttu-id="41afb-134">如果使用可用性群組精靈，您就可以允許精靈一開始同步處理次要複本資料庫，也可以使用備份和還原來手動執行初始化。</span><span class="sxs-lookup"><span data-stu-id="41afb-134">If using the Availability Group Wizard, you can either allow the wizard to initially synchronize the secondary replica databases or you can perform the initialization manually by using backup and restore.</span></span>  
  
 <span data-ttu-id="41afb-135">針對可用性群組建立複寫代理程式將用來連接到目前主要複本的 DNS 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="41afb-135">Create a DNS listener for the availability group that will be used by the replication agents to connect to the current primary.</span></span> <span data-ttu-id="41afb-136">指定的接聽程式名稱將當做原始發行者/已發行資料庫配對的重新導向目標使用。</span><span class="sxs-lookup"><span data-stu-id="41afb-136">The listener name that is specified will be used as the target of redirection for the original publisher/published database pair.</span></span> <span data-ttu-id="41afb-137">例如，如果您要使用 DDL 來設定可用性群組，可以使用下列程式碼範例，針對名為 `MyAG` 的現有可用性群組指定可用性群組接聽程式：</span><span class="sxs-lookup"><span data-stu-id="41afb-137">For example, if you are using DDL to configure the availability group, the following code example can be used to specify an availability group listener for an existing availability group named `MyAG`:</span></span>  
  
```sql
ALTER AVAILABILITY GROUP 'MyAG'   
    ADD LISTENER 'MyAGListenerName' (WITH IP (('10.120.19.155', '255.255.254.0')));  
```  
  
 <span data-ttu-id="41afb-138">如需詳細資訊，請參閱[建立及設定可用性群組 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="41afb-138">For more information, see [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md).</span></span>  
  
##  <a name="3-insure-that-all-of-the-secondary-replica-hosts-are-configured-for-replication"></a><a name="step3"></a><span data-ttu-id="41afb-139">3. 確保所有次要複本主機都設定為複寫</span><span class="sxs-lookup"><span data-stu-id="41afb-139">3. Insure that all of the Secondary Replica Hosts are Configured for Replication</span></span>  
 <span data-ttu-id="41afb-140">在每個次要複本主機上，確認 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 已經設定為支援複寫。</span><span class="sxs-lookup"><span data-stu-id="41afb-140">At each secondary replica host, verify that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been configured to support replication.</span></span> <span data-ttu-id="41afb-141">您可以在每個次要複本主機上執行下列查詢，以便判斷是否已安裝複寫：</span><span class="sxs-lookup"><span data-stu-id="41afb-141">The following query can be run at each secondary replica host to determine whether replication is installed:</span></span>  
  
```sql
USE master;  
GO  
DECLARE @installed int;  
EXEC @installed = sys.sp_MS_replication_installed;  
SELECT @installed;  
```  
  
 <span data-ttu-id="41afb-142">如果 *@installed* 為0，則必須將複寫加入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="41afb-142">If *@installed* is 0, replication must be added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation.</span></span>  
  
##  <a name="4-configure-the-secondary-replica-hosts-as-replication-publishers"></a><a name="step4"></a> <span data-ttu-id="41afb-143">4.將次要複本主機設定為複寫發行者</span><span class="sxs-lookup"><span data-stu-id="41afb-143">4. Configure the Secondary Replica Hosts as Replication Publishers</span></span>  
 <span data-ttu-id="41afb-144">次要複本無法做為複寫發行者或重新發行者，但是您必須設定複寫，才能讓次要複本在容錯移轉之後接管。</span><span class="sxs-lookup"><span data-stu-id="41afb-144">A secondary replica cannot act as a replication publisher or republisher but replication must be configured so that the secondary can take over after a failover.</span></span> <span data-ttu-id="41afb-145">在散發者端，設定每個次要複本主機的散發。</span><span class="sxs-lookup"><span data-stu-id="41afb-145">At the distributor, configure distribution for each secondary replica host.</span></span> <span data-ttu-id="41afb-146">請指定當原始發行者加入至散發者時指定的相同散發資料庫和工作目錄。</span><span class="sxs-lookup"><span data-stu-id="41afb-146">Specify the same distribution database and working directory as was specified when the original publisher was added to the distributor.</span></span> <span data-ttu-id="41afb-147">如果您要使用預存程序來設定散發，請使用 `sp_adddistpublisher`，讓遠端發行者與散發者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="41afb-147">If you are using stored procedures to configure distribution, use `sp_adddistpublisher` to associate the remote publishers with the distributor.</span></span> <span data-ttu-id="41afb-148">如果 *@login* 和 *@password* 已用於原始發行者，請在您加入次要複本主機做為發行者時，為每個指定相同的值。</span><span class="sxs-lookup"><span data-stu-id="41afb-148">If *@login* and *@password* were used for the original publisher, specify the same values for each when you add the secondary replica hosts as publishers.</span></span>  
  
```sql
EXEC sys.sp_adddistpublisher  
    @publisher = 'AGSecondaryReplicaHost',  
    @distribution_db = 'distribution',  
    @working_directory = '\\MyReplShare\WorkingDir',  
    @login = 'MyPubLogin',  
    @password = '**Strong password for publisher**';  
```  
  
 <span data-ttu-id="41afb-149">在每個次要複本主機上，設定散發。</span><span class="sxs-lookup"><span data-stu-id="41afb-149">At each secondary replica host, configure distribution.</span></span> <span data-ttu-id="41afb-150">您可以將原始發行者的散發者識別為遠端散發者。</span><span class="sxs-lookup"><span data-stu-id="41afb-150">Identify the distributor of the original publisher as the remote distributor.</span></span> <span data-ttu-id="41afb-151">請使用當 `sp_adddistributor` 原本在散發者端執行時使用的相同密碼。</span><span class="sxs-lookup"><span data-stu-id="41afb-151">Use the same password as that used when `sp_adddistributor` was run originally at the distributor.</span></span> <span data-ttu-id="41afb-152">如果預存程式正用於設定散發，則 *@password* `sp_adddistributor` 會使用的參數來指定密碼。</span><span class="sxs-lookup"><span data-stu-id="41afb-152">If stored procedures are being used to configure distribution, the *@password* parameter of `sp_adddistributor` is used to specify the password.</span></span>  
  
```sql
EXEC sp_adddistributor   
    @distributor = 'MyDistributor',  
    @password = '**Strong password for distributor**';  
```  
  
 <span data-ttu-id="41afb-153">在每個次要複本主機上，確定資料庫發行集的發送訂閱者顯示成連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="41afb-153">At each secondary replica host, make sure that the push subscribers of the database publications appear as linked servers.</span></span> <span data-ttu-id="41afb-154">如果預存程序正用於設定遠端發行者，請使用 `sp_addlinkedserver`，將訂閱者 (如果原本不存在的話) 當做連結的伺服器加入至發行者。</span><span class="sxs-lookup"><span data-stu-id="41afb-154">If stored procedures are being used to configure the remote publishers, use `sp_addlinkedserver` to add the subscribers (if not already present) as linked servers to the publishers.</span></span>  
  
```sql
EXEC sys.sp_addlinkedserver   
    @server = 'MySubscriber';  
```  
  
##  <a name="5-redirect-the-original-publisher-to-the-ag-listener-name"></a><a name="step5"></a> <span data-ttu-id="41afb-155">5.將原始發行者重新導向至 AG 接聽程式名稱</span><span class="sxs-lookup"><span data-stu-id="41afb-155">5. Redirect the Original Publisher to the AG Listener Name</span></span>  
 <span data-ttu-id="41afb-156">在散發者端的散發資料庫中，執行 `sp_redirect_publisher` 預存程序，以便讓原始發行者和已發行資料庫與可用性群組的可用性群組接聽程式名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="41afb-156">At the distributor, in the distribution database, run the stored procedure `sp_redirect_publisher` to associate the original publisher and the published database with the availability group listener name of the availability group.</span></span>  
  
```sql
USE distribution;  
GO  
EXEC sys.sp_redirect_publisher   
@original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = 'MyAGListenerName';  
```  
  
##  <a name="6-run-the-replication-validation-stored-procedure-to-verify-the-configuration"></a><a name="step6"></a> <span data-ttu-id="41afb-157">6.執行複寫驗證預存程序以確認組態</span><span class="sxs-lookup"><span data-stu-id="41afb-157">6. Run the Replication Validation Stored Procedure to Verify the Configuration</span></span>  
 <span data-ttu-id="41afb-158">在散發者端的散發資料庫中，執行 `sp_validate_replica_hosts_as_publishers` 預存程序，以便確認所有複本主機現在都設定為當做已發行資料庫的發行者。</span><span class="sxs-lookup"><span data-stu-id="41afb-158">At the distributor, in the distribution database, run the stored procedure `sp_validate_replica_hosts_as_publishers` to verify that all replica hosts are now configured to serve as publishers for the published database.</span></span>  
  
```sql
USE distribution;  
GO  
DECLARE @redirected_publisher sysname;  
EXEC sys.sp_validate_replica_hosts_as_publishers  
    @original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = @redirected_publisher output;  
```  
  
 <span data-ttu-id="41afb-159">在每個可用性群組複本主機上，`sp_validate_replica_hosts_as_publishers` 預存程序應該從具有足夠授權的登入執行，以便查詢可用性群組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="41afb-159">The stored procedure `sp_validate_replica_hosts_as_publishers` should be run from a login with sufficient authorization at each availability group replica host to query for information about the availability group.</span></span> <span data-ttu-id="41afb-160">與不同的是 `sp_validate_redirected_publisher` ，它會使用呼叫端的認證，而且不會使用 msdb.dbo.msdistpublishers 中保留的登入來連接可用性群組複本。</span><span class="sxs-lookup"><span data-stu-id="41afb-160">Unlike `sp_validate_redirected_publisher`, it uses the credentials of the caller and does not use the login retained in msdb.dbo.MSdistpublishers to connect to the availability group replicas.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41afb-161">在驗證不允許讀取存取或需要指定讀取意圖的次要複本主機時，`sp_validate_replica_hosts_as_publishers` 會失敗並發生下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="41afb-161">`sp_validate_replica_hosts_as_publishers` will fail with the following error when validating secondary replica hosts that do not allow read access, or require read intent to be specified.</span></span>  
>   
>  <span data-ttu-id="41afb-162">訊息 21899，層級 11，狀態 1，程序 `sp_hadr_verify_subscribers_at_publisher`，行 109</span><span class="sxs-lookup"><span data-stu-id="41afb-162">Msg 21899, Level 11, State 1, Procedure `sp_hadr_verify_subscribers_at_publisher`, Line 109</span></span>  
>   
>  <span data-ttu-id="41afb-163">在重新導向的發行者 'MyReplicaHostName' 上用以判斷原始發行者 'MyOriginalPublisher' 的訂閱者是否有 sysserver 項目的查詢失敗，發生錯誤 '976'，錯誤訊息為「錯誤 976，層級 14，狀態 1，訊息：目標資料庫 'MyPublishedDB' 正參與可用性群組，目前無法供查詢存取。</span><span class="sxs-lookup"><span data-stu-id="41afb-163">The query at the redirected publisher 'MyReplicaHostName' to determine whether there were sysserver entries for the subscribers of the original publisher 'MyOriginalPublisher' failed with error '976', error message 'Error 976, Level 14, State 1, Message: The target database, 'MyPublishedDB', is participating in an availability group and is currently not accessible for queries.</span></span> <span data-ttu-id="41afb-164">資料移動已暫停，或者可用性複本無法進行讀取存取。</span><span class="sxs-lookup"><span data-stu-id="41afb-164">Either data movement is suspended or the availability replica is not enabled for read access.</span></span> <span data-ttu-id="41afb-165">若要允許唯讀存取可用性群組中的這個資料庫和其他資料庫，請啟用群組中一個或多個次要可用性複本的讀取存取。</span><span class="sxs-lookup"><span data-stu-id="41afb-165">To allow read-only access to this and other databases in the availability group, enable read access to one or more secondary availability replicas in the group.</span></span>  <span data-ttu-id="41afb-166">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》中的＜`ALTER AVAILABILITY GROUP` 陳述式＞」。</span><span class="sxs-lookup"><span data-stu-id="41afb-166">For more information, see the `ALTER AVAILABILITY GROUP` statement in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.'.</span></span>  
>   
>  <span data-ttu-id="41afb-167">複本主機 'MyReplicaHostName' 發生了一個或多個發行者驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="41afb-167">One or more publisher validation errors were encountered for replica host 'MyReplicaHostName'.</span></span>  
  
 <span data-ttu-id="41afb-168">這是預期行為。</span><span class="sxs-lookup"><span data-stu-id="41afb-168">This is expected behavior.</span></span> <span data-ttu-id="41afb-169">您必須直接在主機上查詢 sysserver 項目，藉以確認訂閱者伺服器項目是否存在這些次要複本主機上。</span><span class="sxs-lookup"><span data-stu-id="41afb-169">You must verify the presence of the subscriber server entries at these secondary replica hosts by querying for the sysserver entries directly at the host.</span></span>  
  
##  <a name="7-add-the-original-publisher-to-replication-monitor"></a><a name="step7"></a> <span data-ttu-id="41afb-170">7.將原始發行者加入至複寫監視器</span><span class="sxs-lookup"><span data-stu-id="41afb-170">7. Add the Original Publisher to Replication Monitor</span></span>  
 <span data-ttu-id="41afb-171">在每個可用性群組複本上，將原始發行者加入至複寫監視器。</span><span class="sxs-lookup"><span data-stu-id="41afb-171">At each availability group replica, add the original publisher to Replication Monitor.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="41afb-172">相關工作</span><span class="sxs-lookup"><span data-stu-id="41afb-172">Related Tasks</span></span>  
 <span data-ttu-id="41afb-173">**複寫**</span><span class="sxs-lookup"><span data-stu-id="41afb-173">**Replication**</span></span>  
  
-   [<span data-ttu-id="41afb-174">維護 AlwaysOn 發行集資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-174">Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;</span></span>](maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [<span data-ttu-id="41afb-175">複寫、變更追蹤、變更資料捕獲，以及 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-175">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [<span data-ttu-id="41afb-176">複寫管理常見問題集</span><span class="sxs-lookup"><span data-stu-id="41afb-176">Replication Administration FAQ</span></span>](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
 <span data-ttu-id="41afb-177">**若要建立並設定可用性群組**</span><span class="sxs-lookup"><span data-stu-id="41afb-177">**To create and configure an availability group**</span></span>  
  
-   [<span data-ttu-id="41afb-178">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-178">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="41afb-179">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-179">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="41afb-180">建立可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-180">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="41afb-181">建立可用性群組 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-181">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="41afb-182">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-182">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="41afb-183">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-183">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="41afb-184">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-184">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="41afb-185">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-185">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="41afb-186">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-186">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="41afb-187">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41afb-187">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="41afb-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41afb-188">See Also</span></span>  
 <span data-ttu-id="41afb-189">[AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="41afb-189">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="41afb-190">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41afb-190">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="41afb-191">[AlwaysOn 可用性群組：互通性 (SQL Server) ](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41afb-191">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 [<span data-ttu-id="41afb-192">SQL Server 複寫</span><span class="sxs-lookup"><span data-stu-id="41afb-192">SQL Server Replication</span></span>](../../../relational-databases/replication/sql-server-replication.md)  
