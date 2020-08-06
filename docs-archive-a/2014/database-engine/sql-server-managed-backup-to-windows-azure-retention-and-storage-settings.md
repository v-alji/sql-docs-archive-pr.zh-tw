---
title: SQL Server 受管理的備份至 Azure-保留和儲存設定 |Microsoft Docs
description: 本主題描述如何將 SQL Server Managed 備份設定為資料庫的 Microsoft Azure，以及設定實例的預設設定。
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8ebdb81f8aa9edb9cd9326bcb1d286d5d3fe632c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705405"
---
# <a name="sql-server-managed-backup-to-azure---retention-and-storage-settings"></a><span data-ttu-id="8c693-103">SQL Server Managed Backup 到 Azure - 保留和儲存體設定</span><span class="sxs-lookup"><span data-stu-id="8c693-103">SQL Server Managed Backup to Azure - Retention and Storage Settings</span></span>
  <span data-ttu-id="8c693-104">本主題說明設定資料庫之 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 及設定執行個體之預設設定的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="8c693-104">This topic describes the basic steps to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database and to configure default settings for the instance.</span></span> <span data-ttu-id="8c693-105">本主題也描述為執行個體暫停及繼續 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服務的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="8c693-105">The topic also describes the steps necessary to pause and resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services for the instance.</span></span>  
  
 <span data-ttu-id="8c693-106">如需設定的完整逐步解說 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，請參閱[設定 SQL Server 受管理的備份至 azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md)和[針對可用性群組設定 SQL Server 受控備份至 azure](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="8c693-106">For a complete walkthrough of setting up [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] see [Setting up SQL Server Managed Backup to Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) and [Setting up SQL Server Managed Backup to Azure for Availability Groups](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8c693-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="8c693-107">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8c693-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="8c693-108">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8c693-109">請勿對目前正在使用維護計劃或記錄傳送的資料庫啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8c693-109">Do not enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on databases that are currently using maintenance plans or log shipping.</span></span> <span data-ttu-id="8c693-110">如需有關互通性和與其他 SQL Server 功能共存的詳細資訊，請參閱[SQL Server 受控備份至 Azure：互通性與共存](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)</span><span class="sxs-lookup"><span data-stu-id="8c693-110">For more information on interoperability and coexistence with other SQL Server features, see [SQL Server Managed Backup to Azure: Interoperability and Coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="8c693-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="8c693-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="8c693-112">SQL Server Agent 應在執行中。</span><span class="sxs-lookup"><span data-stu-id="8c693-112">SQL Server Agent should be running.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="8c693-113">如果 SQL Server Agent 已停止一段時間然後重新啟動，您可能會看見備份活動增加 (視 SQL Agent 停止和啟動之間經過的時間長度而定)，而且可能會有記錄備份積存等待執行。</span><span class="sxs-lookup"><span data-stu-id="8c693-113">If SQL Server Agent is stopped for a period of time and then restarted, you may see an increased backup activity depending on the length of time elapsed between the stop and start of SQL Agent, and there might be a backlog of log backups waiting to run.</span></span> <span data-ttu-id="8c693-114">請考慮將 SQL Server Agent 設定為啟動時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="8c693-114">Consider configuring SQL Server Agent to start automatically on start up.</span></span>  
  
-   <span data-ttu-id="8c693-115">在設定之前，您應該先建立 Azure 儲存體帳戶，以及將驗證資訊儲存到儲存體帳戶的 SQL 認證 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8c693-115">A Azure storage account and a SQL Credential that stores the authentication information to the storage account should both be created before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="8c693-116">如需詳細資訊，請參閱 [SQL Server 備份至 URL](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) 主題中的 **Introduction to Key Components and Concepts** 一節，以及 [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)。</span><span class="sxs-lookup"><span data-stu-id="8c693-116">For more information see [Introduction to Key Components and Concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) section of the **SQL Server Backup to URL** topic, and [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="8c693-117">會建立必要的容器以儲存備份。</span><span class="sxs-lookup"><span data-stu-id="8c693-117">creates the necessary containers to store the backups.</span></span> <span data-ttu-id="8c693-118">使用「電腦名稱稱-實例名稱」格式建立容器名稱。</span><span class="sxs-lookup"><span data-stu-id="8c693-118">The container name is created using 'machine name-instance name' format.</span></span> <span data-ttu-id="8c693-119">AlwaysOn 可用性群組的容器會以可用性群組的 GUID 命名。</span><span class="sxs-lookup"><span data-stu-id="8c693-119">For AlwaysOn Availability Groups the container is named using the GUID of the availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8c693-120">Security</span><span class="sxs-lookup"><span data-stu-id="8c693-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8c693-121">權限</span><span class="sxs-lookup"><span data-stu-id="8c693-121">Permissions</span></span>  
 <span data-ttu-id="8c693-122">若要執行啟用的預存程式 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，您必須是 `System Administrator` 具有**ALTER ANY CREDENTIAL**許可權的**db_backupoperator**資料庫角色中的或成員，以及 `EXECUTE` **sp_delete_backuphistory**和 `smart_admin.sp_backup_master_switch` 預存程式的許可權。</span><span class="sxs-lookup"><span data-stu-id="8c693-122">To run the stored procedures that enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], you must be a  either a `System Administrator` or  member  in the **db_backupoperator** database role with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on the **sp_delete_backuphistory**, and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  <span data-ttu-id="8c693-123">用於檢閱現有設定的預存程序及函式，通常需要具備預存程序的 `Execute` 權限及函式的 `Select`。</span><span class="sxs-lookup"><span data-stu-id="8c693-123">Stored procedures and functions used to review the existing settings typically require `Execute` permissions on the stored procedure and `Select` on the function respectively.</span></span>  
  

  
###  <a name="considerations-for-enabling-ss_smartbackup-for-databases-and-instances"></a><a name="Considerations"></a><span data-ttu-id="8c693-124">針對 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 資料庫和實例啟用的考慮</span><span class="sxs-lookup"><span data-stu-id="8c693-124">Considerations for enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for Databases and Instances</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="8c693-125">可以為了個別資料庫而分別啟用，或者為了整個執行個體而啟用。</span><span class="sxs-lookup"><span data-stu-id="8c693-125">can be enabled for individual databases separately or for the entire instance.</span></span> <span data-ttu-id="8c693-126">這些選擇取決於實例上資料庫的復原能力需求、管理多個資料庫和實例的需求，以及策略性地使用 Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="8c693-126">The choices depend on the recoverability requirements for the databases on the instance, requirements for managing multiple databases and instances, and using Azure storage strategically.</span></span>  
  
#### <a name="enabling-ss_smartbackup-at-the-database-level"></a><span data-ttu-id="8c693-127">正在資料庫層級啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-127">Enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Database Level</span></span>  
 <span data-ttu-id="8c693-128">如果資料庫有特定的備份需求與保留週期 (復原能力 SLA)，並且和執行個體上的其他資料庫不同，請在資料庫層級為此資料庫設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8c693-128">If a database has specific requirements for backup and retention period (recoverability SLA) that is different from other databases on the instance, configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level for this database.</span></span> <span data-ttu-id="8c693-129">資料庫層級設定會覆寫執行個體層級的組態設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-129">Database level settings override instance level configuration settings.</span></span> <span data-ttu-id="8c693-130">但相同的執行個體可以並用這兩個選項。</span><span class="sxs-lookup"><span data-stu-id="8c693-130">However both these options can be used together on the same instance.</span></span> <span data-ttu-id="8c693-131">下列清單列有在資料庫層級上啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的優點及注意事項。</span><span class="sxs-lookup"><span data-stu-id="8c693-131">Following is a list of advantages and considerations when enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level.</span></span>  
  
-   <span data-ttu-id="8c693-132">更為精細：分隔每個資料庫的組態設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-132">More granular: Separate configuration settings for each database.</span></span> <span data-ttu-id="8c693-133">可以針對不同的資料庫支援不同的保留週期。</span><span class="sxs-lookup"><span data-stu-id="8c693-133">Can support different retention periods for individual databases.</span></span>  
  
-   <span data-ttu-id="8c693-134">覆寫資料庫的執行個體層級設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-134">Overrides instance level settings for the database.</span></span>  
  
-   <span data-ttu-id="8c693-135">透過選取要備份的個別資料庫，可用來降低儲存成本。</span><span class="sxs-lookup"><span data-stu-id="8c693-135">Can be used to reduce storage costs by selecting individual databases to be backed up.</span></span>  
  
-   <span data-ttu-id="8c693-136">需要管理每個資料庫</span><span class="sxs-lookup"><span data-stu-id="8c693-136">Requires managing each database</span></span>  
  
#### <a name="enabling-ss_smartbackup-at-the-instance-level-with-default-settings"></a><span data-ttu-id="8c693-137">使用預設設定在執行個體層級啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-137">Enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Instance Level with Default Settings</span></span>  
 <span data-ttu-id="8c693-138">如果大部分執行個體上的資料庫都有相同的備份和保留原則需求，或者如果您想要新的資料庫執行個體在建立時自動備份，請使用此設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-138">Use this setting if most of the databases in the instance have the same requirements for backup and retention policies, or if you want new database instances to automatically be backed up on creation.</span></span> <span data-ttu-id="8c693-139">一些未套用原則的資料庫仍可個別加以設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-139">A few databases that are exception to the policy can still be configured individually.</span></span> <span data-ttu-id="8c693-140">在執行個體層級上啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 時，以下為優點和考量清單。</span><span class="sxs-lookup"><span data-stu-id="8c693-140">Following is a list of advantages and considerations when enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the instance level.</span></span>  
  
-   <span data-ttu-id="8c693-141">在執行個體層級的自動化：常見的設定會自動套用於之後加入的新資料庫。</span><span class="sxs-lookup"><span data-stu-id="8c693-141">Automation at the instance level: Common settings applied to automatically for new databases added thereafter.</span></span>  
  
-   <span data-ttu-id="8c693-142">新資料庫於執行個體上建立後，它們很快就會自動備份</span><span class="sxs-lookup"><span data-stu-id="8c693-142">New databases will be automatically backed up soon after they are created on the instances</span></span>  
  
-   <span data-ttu-id="8c693-143">可以套用至具有相同保留週期需求的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8c693-143">Can be applied to databases that have the same retention period requirements.</span></span>  
  
-   <span data-ttu-id="8c693-144">即使已在執行個體層級啟用使用預設設定的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，您仍可設定需要不同保留週期的各個資料庫。</span><span class="sxs-lookup"><span data-stu-id="8c693-144">You can still configure individual databases that require a different retention period even with [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] backup enabled at in instance level with default settings.</span></span> <span data-ttu-id="8c693-145">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]如果您不想要使用 Azure 儲存體來進行備份，您也可以停用資料庫的。</span><span class="sxs-lookup"><span data-stu-id="8c693-145">You can also disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for databases if you do not intend to use Azure storage for the backups.</span></span>  
  
##  <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><a name="DatabaseConfigure"></a><span data-ttu-id="8c693-146">針對資料庫啟用和設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-146">Enable and Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a Database</span></span>  
 <span data-ttu-id="8c693-147">系統預存程序 `smart_admin.sp_set_db_backup` 可用於為特定資料庫啟用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-147">The system stored procedure `smart_admin.sp_set_db_backup` is used to enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database.</span></span> <span data-ttu-id="8c693-148">第一次啟用資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 時，除了啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]之外，還必須指定下列資訊︰</span><span class="sxs-lookup"><span data-stu-id="8c693-148">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the first time on the database, the following information must be specified in addition to enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:</span></span>  
  
-   <span data-ttu-id="8c693-149">資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c693-149">The name of the database.</span></span>  
  
-   <span data-ttu-id="8c693-150">保留週期。</span><span class="sxs-lookup"><span data-stu-id="8c693-150">The retention period.</span></span>  
  
-   <span data-ttu-id="8c693-151">用來向 Azure 儲存體帳戶進行驗證的 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="8c693-151">SQL Credential used to authenticate to the Azure storage account.</span></span>  
  
-   <span data-ttu-id="8c693-152">請指定不要使用\* \@ encryption_algorithm\*  =  **NO_ENCRYPTION**加密，或是指定支援的加密演算法。</span><span class="sxs-lookup"><span data-stu-id="8c693-152">Either specify not to encrypt using *\@encryption_algorithm* = **NO_ENCRYPTION** or specify a supported encryption algorithm.</span></span> <span data-ttu-id="8c693-153">如需加密的詳細資訊，請參閱＜ [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8c693-153">For more information on encryption, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
 <span data-ttu-id="8c693-154">只能透過 Transact-SQL 支援資料庫層級設定的[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-154">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for database level configuration is only supported through Transact-SQL.</span></span>  
  
 <span data-ttu-id="8c693-155">啟用資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 之後，此資訊會被保存。</span><span class="sxs-lookup"><span data-stu-id="8c693-155">Once [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for a database this information is persisted.</span></span> <span data-ttu-id="8c693-156">如果要變更組態，只需要資料庫名稱和您要變更的設定；如果未指定其他參數， [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 將會保留其他參數現有的值。</span><span class="sxs-lookup"><span data-stu-id="8c693-156">If you are changing the configuration, only the database name and the setting you want to change is required, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] retains the existing values for other parameters when not specified.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8c693-157">在設定資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 前，它對現有的組態 (如果有的話) 也許會有幫助。</span><span class="sxs-lookup"><span data-stu-id="8c693-157">Before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on a database it might be useful to existing configuration if any.</span></span> <span data-ttu-id="8c693-158">檢閱資料庫組態設定的步驟，於本節稍後說明。</span><span class="sxs-lookup"><span data-stu-id="8c693-158">The step to reviewing configuration settings for a database is explained later in this section.</span></span>  
  
-   <span data-ttu-id="8c693-159">**使用 Transact-sql：**</span><span class="sxs-lookup"><span data-stu-id="8c693-159">**Using Transact-SQL:**</span></span>  
  
     <span data-ttu-id="8c693-160">如果您是 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 第一次啟用，所需的參數為： \* \@ database_name*、 \* \@ credential_name* \* \@ encryption_algorithm*， \* \@ enable_backup* \* \@ storage_url\*參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="8c693-160">If you are enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the first time, the required parameters are: *\@database_name*, *\@credential_name*, *\@encryption_algorithm*,  *\@enable_backup* The *\@storage_url* parameter is optional.</span></span> <span data-ttu-id="8c693-161">如果您未提供參數的值，則 @storage_url 會使用 SQL 認證中的儲存體帳戶資訊來衍生值。</span><span class="sxs-lookup"><span data-stu-id="8c693-161">If you do not provide a value for  the @storage_url parameter, the value is derived using the storage account information from the SQL Credential.</span></span> <span data-ttu-id="8c693-162">如有提供儲存體 URL，應只提供儲存體帳戶根目錄的 URL，而且必須符合所指定之 SQL 認證中的資訊。</span><span class="sxs-lookup"><span data-stu-id="8c693-162">If you provide the storage URL you should only provide the URL for the root of the storage account, and must match the information in the SQL Credential you specified.</span></span>  
  
    1.  <span data-ttu-id="8c693-163">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-163">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
    2.  <span data-ttu-id="8c693-164">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8c693-164">From the Standard bar, click **New Query**.</span></span>  
  
    3.  <span data-ttu-id="8c693-165">將下列範例複製並貼入查詢視窗中，然後按一下 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="8c693-165">Copy and paste the following example into the query window and click `Execute`.</span></span> <span data-ttu-id="8c693-166">這個範例會啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 資料庫 ' TestDB ' 的。</span><span class="sxs-lookup"><span data-stu-id="8c693-166">This example enables [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the database 'TestDB'.</span></span> <span data-ttu-id="8c693-167">保留週期設為 30 天。</span><span class="sxs-lookup"><span data-stu-id="8c693-167">The retention period is set to 30 days.</span></span> <span data-ttu-id="8c693-168">此範例會指定加密演算法和加密程式資訊來使用加密選項。</span><span class="sxs-lookup"><span data-stu-id="8c693-168">This sample uses the encryption option by specifying the encryption algorithm and the encryptor information.</span></span>  
  
    ```sql
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8c693-169">保留週期可設為 1 到 30 天之間的任何值。</span><span class="sxs-lookup"><span data-stu-id="8c693-169">The retention period can be set to any value from 1 to 30 days.</span></span>  
    >   
    >  <span data-ttu-id="8c693-170">如需有關建立憑證以進行加密的詳細資訊，請參閱＜ [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)＞中的「建立備份憑證」步驟。</span><span class="sxs-lookup"><span data-stu-id="8c693-170">For more information on creating a certificate for encryption, see the Create a Backup Certificate step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
     <span data-ttu-id="8c693-171">如需此預存程式的詳細資訊，請參閱[smart_admin。 set_db_backup &#40;transact-sql&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="8c693-171">For more information on this stored procedure, see [smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)</span></span>  
  
     <span data-ttu-id="8c693-172">若要檢閱資料庫的組態設定，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="8c693-172">To review the configuration settings for a database use the following query:</span></span>  
  
    ```sql
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="enable-and-configure-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceConfigure"></a><span data-ttu-id="8c693-173">啟用和設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 實例的預設設定</span><span class="sxs-lookup"><span data-stu-id="8c693-173">Enable and Configure Default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings for the Instance</span></span>  
 <span data-ttu-id="8c693-174">您可以透過 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 兩種方式在實例層級啟用和設定預設設定：使用系統預存程式 `smart_admin.set_instance_backup` 或**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="8c693-174">You can enable and configure default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings at the instance level in two ways:  By using the system stored procedure `smart_admin.set_instance_backup` or **SQL Server Management Studio**.</span></span> <span data-ttu-id="8c693-175">這兩種方法說明如下：</span><span class="sxs-lookup"><span data-stu-id="8c693-175">The two methods are explained below:</span></span>  
  
 <span data-ttu-id="8c693-176">**smart_admin. set_instance_backup：**。</span><span class="sxs-lookup"><span data-stu-id="8c693-176">**smart_admin.set_instance_backup:**.</span></span> <span data-ttu-id="8c693-177">藉由為\* \@ enable_backup\*參數指定**1**的值，您就可以啟用備份並設定預設設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-177">By specifying the value **1** for *\@enable_backup* parameter, you can enable backup and set the default configurations.</span></span> <span data-ttu-id="8c693-178">套用在執行個體層級之後，這些預設設定值會套用至加入此執行個體的所有新資料庫。</span><span class="sxs-lookup"><span data-stu-id="8c693-178">Once applied at the instance level, these default settings are applied to any new database that is added to this instance.</span></span>  <span data-ttu-id="8c693-179">第一次啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 時，除了啟用執行個體的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 之外，還必須提供下列資訊︰</span><span class="sxs-lookup"><span data-stu-id="8c693-179">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the first time, the following information must be provided in addition to enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on the instance:</span></span>  
  
-   <span data-ttu-id="8c693-180">保留週期。</span><span class="sxs-lookup"><span data-stu-id="8c693-180">The retention period.</span></span>  
  
-   <span data-ttu-id="8c693-181">用來向 Azure 儲存體帳戶進行驗證的 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="8c693-181">SQL Credential used to authenticate to the Azure storage account.</span></span>  
  
-   <span data-ttu-id="8c693-182">加密選項。</span><span class="sxs-lookup"><span data-stu-id="8c693-182">The encryption option.</span></span> <span data-ttu-id="8c693-183">請指定不要使用\* \@ encryption_algorithm\*  =  **NO_ENCRYPTION**加密，或是指定支援的加密演算法。</span><span class="sxs-lookup"><span data-stu-id="8c693-183">Either specify not to encrypt using *\@encryption_algorithm* = **NO_ENCRYPTION** or specify a supported encryption algorithm.</span></span> <span data-ttu-id="8c693-184">如需加密的詳細資訊，請參閱＜ [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8c693-184">For more information on encryption, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
 <span data-ttu-id="8c693-185">啟用之後，這些設定會保存。</span><span class="sxs-lookup"><span data-stu-id="8c693-185">Once enabled these settings are persisted.</span></span> <span data-ttu-id="8c693-186">如果要變更組態，只需要資料庫名稱和您要變更的設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-186">If you are changing the configuration, only the database name and the setting you want to change is required.</span></span> <span data-ttu-id="8c693-187">如果未指定，[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]會保留現有的值。</span><span class="sxs-lookup"><span data-stu-id="8c693-187">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] retains the existing values when not specified.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8c693-188">在設定執行個體的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 前，它對檢查現有的組態 (如果有的話) 也許會有幫助。</span><span class="sxs-lookup"><span data-stu-id="8c693-188">Before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on an instance, it might be useful to check for existing configuration, if any.</span></span> <span data-ttu-id="8c693-189">檢閱資料庫組態設定的步驟，於本節稍後說明。</span><span class="sxs-lookup"><span data-stu-id="8c693-189">The step to reviewing configuration settings for a database is explained later in this section.</span></span>  
  
 <span data-ttu-id="8c693-190">**SQL Server Management Studio** ：若要在 SQL Server Management Studio 中執行這項工作，請移至 [物件總管]，再展開 **[管理]** 節點，並以滑鼠右鍵按一下 **[Managed Backup]**。</span><span class="sxs-lookup"><span data-stu-id="8c693-190">**SQL Server Management Studio:** To do this task in SQL Server Management Studio, go the object explorer, expand the **Management** node, and right click on **Managed Backup**.</span></span> <span data-ttu-id="8c693-191">選取 [設定] 。</span><span class="sxs-lookup"><span data-stu-id="8c693-191">Select **Configure**.</span></span> <span data-ttu-id="8c693-192">這樣會開啟 **[Managed Backup]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8c693-192">This opens the **Managed Backup** dialog.</span></span> <span data-ttu-id="8c693-193">使用此對話方塊可指定保留週期、SQL 認證、儲存體 URL 和加密設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-193">Use this dialog to specify the retention period, SQL Credential, Storage URL, and the encryption settings.</span></span> <span data-ttu-id="8c693-194">如需此對話方塊的特定說明，請參閱[設定受管理的備份 &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="8c693-194">For specific help with this dialog, see [Configure Managed Backup &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).</span></span>  
  
#### <a name="using-transact-sql"></a><span data-ttu-id="8c693-195">使用 TRANSACT-SQL</span><span class="sxs-lookup"><span data-stu-id="8c693-195">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="8c693-196">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-196">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8c693-197">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8c693-197">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8c693-198">將下列範例複製並貼入查詢視窗中，然後按一下 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="8c693-198">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8c693-199">保留週期可設為 1 到 30 天之間的任何值。</span><span class="sxs-lookup"><span data-stu-id="8c693-199">The retention period can be set to any value from 1 to 30 days.</span></span>  
>   
>  <span data-ttu-id="8c693-200">如需有關建立憑證以進行加密的詳細資訊，請參閱＜ [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)＞中的「建立備份憑證」步驟。</span><span class="sxs-lookup"><span data-stu-id="8c693-200">For more information on creating a certificate for encryption, see the Create a Backup Certificate step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
 <span data-ttu-id="8c693-201">若要檢視執行個體的預設組態設定，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="8c693-201">To view the default configuration settings for the instance, use the following query:</span></span>  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();
```  
  
#### <a name="using-powershell"></a><span data-ttu-id="8c693-202">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c693-202">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="8c693-203">啟動 PowerShell 執行個體</span><span class="sxs-lookup"><span data-stu-id="8c693-203">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="8c693-204">修改到符合您的設定後，執行下列指令碼。</span><span class="sxs-lookup"><span data-stu-id="8c693-204">Run the following script after modifying it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -BackupEnabled $True -BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8c693-205">當您進行預設設定後，建立新的資料庫時，可能需要花費 15 分鐘對資料庫進行預設設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-205">When you create a new database after configuring the default settings, it may take up to 15 minutes for the database to be configured with the default settings.</span></span> <span data-ttu-id="8c693-206">這也適用於從 **Simple** 變更至 **Full** 或 **Bulk-Logged** 復原模式的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8c693-206">This also applies to databases that are changed from **Simple** to **Full** or **Bulk-Logged** recovery model.</span></span>  
  
##  <a name="disable-ss_smartbackup-for-a-database"></a><a name="DatabaseDisable"></a> <span data-ttu-id="8c693-207">停用資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-207">Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database</span></span>  
 <span data-ttu-id="8c693-208">您可以使用 `sp_set_db_backup` 系統預存程序來停用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-208">You can disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings by using the `sp_set_db_backup` system stored procedure.</span></span> <span data-ttu-id="8c693-209">\* \@ Enableparameter\*是用來啟用和停用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 特定資料庫的設定，其中1會啟用，而0會停用設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-209">The *\@enableparameter* is used to enable and disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configurations for a specific database, where 1 enables and 0 disables the configuration settings.</span></span>  
  
#### <a name="to-disable-ss_smartbackup-for-a-specific-database"></a><span data-ttu-id="8c693-210">停用特定資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="8c693-210">To Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database:</span></span>  
  
1.  <span data-ttu-id="8c693-211">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-211">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8c693-212">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8c693-212">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8c693-213">將下列範例複製並貼入查詢視窗中，然後按一下 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="8c693-213">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO
```  
  
##  <a name="disable-ss_smartbackup-for-all-the-databases-on-the-instance"></a><a name="DatabaseAllDisable"></a> <span data-ttu-id="8c693-214">停用執行個體上所有資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-214">Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for all the databases on the Instance</span></span>  
 <span data-ttu-id="8c693-215">從近期在執行個體上啟用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的所有資料庫中，若您要停用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 組態設定，可使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="8c693-215">The following procedure is for when you want to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration settings from all the databases that currently have [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled on the instance.</span></span>  <span data-ttu-id="8c693-216">組態設定 (例如儲存體 URL、保留項目和 SQL 認證) 都會保留在中繼資料中，如果稍後啟用資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 即可使用。</span><span class="sxs-lookup"><span data-stu-id="8c693-216">The configuration settings like the storage URL, retention, and the SQL Credential will remain in the metadata and can be used  if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the database at a later time.</span></span> <span data-ttu-id="8c693-217">如果您只是想暫停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服務，可使用主切換，本主題的以下章節會解釋。</span><span class="sxs-lookup"><span data-stu-id="8c693-217">If you want to just pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services temporarily, you can use the master switch explained in the following sections later in this topic.</span></span>  
  
#### <a name="to-disable-ss_smartbackupfor-all-the-databases"></a><span data-ttu-id="8c693-218">停用所有資料庫的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="8c693-218">To disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]for all the databases:</span></span>  
  
1.  <span data-ttu-id="8c693-219">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-219">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8c693-220">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8c693-220">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8c693-221">將下列範例複製並貼入查詢視窗中，然後按一下 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="8c693-221">Copy and paste the following example into the query window and click `Execute`.</span></span> <span data-ttu-id="8c693-222">下列範例會指出是否已在執行個體層級設定[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，以及該執行個體上，所有已經啟用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]的資料庫，並會執行系統預存程序 `sp_set_db_backup`，以停用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-222">The following example identifies if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured at the instance level and all the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled databases on the instance, and executes the system stored procedure `sp_set_db_backup` to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span>  
  
```sql
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames 
       select @rowid = min(RowID) FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END
```  
  
 <span data-ttu-id="8c693-223">若要檢閱執行個體上所有資料庫的組態設定，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="8c693-223">To review the configuration settings for all the databases on the instance, use the following query:</span></span>  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO
```  
  
##  <a name="disable-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceDisable"></a> <span data-ttu-id="8c693-224">停用執行個體的預設 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 設定</span><span class="sxs-lookup"><span data-stu-id="8c693-224">Disable Default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings for the Instance</span></span>  
 <span data-ttu-id="8c693-225">執行個體層級的預設設定會套用到建立在該執行個體上的所有新資料庫。</span><span class="sxs-lookup"><span data-stu-id="8c693-225">Default settings at the instance level apply to all new databases created on that instance.</span></span>  <span data-ttu-id="8c693-226">如果您不再需要或要求預設設定，可以使用 **smart_admin.sp_set_instance_backup** 系統預存程序以停用此組態。</span><span class="sxs-lookup"><span data-stu-id="8c693-226">If you no longer need or require default settings, you can disable this configuration by using the **smart_admin.sp_set_instance_backup** System stored procedure.</span></span> <span data-ttu-id="8c693-227">停用不會移除其他組態設定，像是儲存體 URL、保留設定或 SQL 認證名稱。</span><span class="sxs-lookup"><span data-stu-id="8c693-227">Disabling does not remove the other configuration settings like the storage URL, retention setting, or the SQL Credential name.</span></span> <span data-ttu-id="8c693-228">如果稍後啟用執行個體的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，將會使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="8c693-228">These settings will be used if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the instance at a later time.</span></span>  
  
#### <a name="to-disable-ss_smartbackup-default-configuration-settings"></a><span data-ttu-id="8c693-229">停用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 預設組態設定：</span><span class="sxs-lookup"><span data-stu-id="8c693-229">To disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] default configuration settings:</span></span>  
  
1.  <span data-ttu-id="8c693-230">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-230">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8c693-231">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8c693-231">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8c693-232">將下列範例複製並貼入查詢視窗中，然後按一下 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="8c693-232">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
    ```sql
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO
    ```  
  
#### <a name="using-powershell"></a><span data-ttu-id="8c693-233">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c693-233">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="8c693-234">啟動 PowerShell 執行個體</span><span class="sxs-lookup"><span data-stu-id="8c693-234">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="8c693-235">執行下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="8c693-235">Run the following script:</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Set-SqlSmartAdmin -BackupEnabled $False  
    ```  
  
##  <a name="pause-ss_smartbackup-at-the-instance-level"></a><a name="InstancePause"></a> <span data-ttu-id="8c693-236">在執行個體層級暫停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-236">Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Instance Level</span></span>  
 <span data-ttu-id="8c693-237">有些時候，您可能會需要暫停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服務一段時間。</span><span class="sxs-lookup"><span data-stu-id="8c693-237">There might be times when you need to temporarily pause the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services for a short period time.</span></span>  <span data-ttu-id="8c693-238">`smart_admin.sp_backup_master_switch` 系統預存程序可讓您在執行個體層級停用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="8c693-238">The `smart_admin.sp_backup_master_switch` system stored procedure allows you to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] service at the instance level.</span></span>  <span data-ttu-id="8c693-239">使用同一個預存程序繼續執行 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-239">The same stored procedure is used to resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="8c693-240">@state 參數可用來定義是否應該關閉或開啟 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-240">The @state parameter is used to define whether [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] should be turned off or on.</span></span>  
  
#### <a name="to-pause-ss_smartbackup-services-using-transact-sql"></a><span data-ttu-id="8c693-241">使用 Transact-SQL 暫停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服務：</span><span class="sxs-lookup"><span data-stu-id="8c693-241">To Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Services Using Transact-SQL:</span></span>  
  
1.  <span data-ttu-id="8c693-242">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-242">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8c693-243">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8c693-243">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8c693-244">將下列範例複製並貼入查詢視窗中，然後按一下`Execute`</span><span class="sxs-lookup"><span data-stu-id="8c693-244">Copy and paste the following example into the query window and then click `Execute`</span></span>  
  
```sql
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-ss_smartbackup-using-powershell"></a><span data-ttu-id="8c693-245">使用 PowerShell 暫停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-245">To pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using PowerShell</span></span>  
  
1.  <span data-ttu-id="8c693-246">啟動 PowerShell 執行個體</span><span class="sxs-lookup"><span data-stu-id="8c693-246">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="8c693-247">修改到符合您的設定後，執行下列指令碼。</span><span class="sxs-lookup"><span data-stu-id="8c693-247">Run the following script after you modify it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $False  
    ```  
  
#### <a name="to-resume-ss_smartbackup-using-transact-sql"></a><span data-ttu-id="8c693-248">使用 Transact-SQL 繼續進行 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-248">To resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="8c693-249">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c693-249">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8c693-250">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8c693-250">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8c693-251">將下列範例複製並貼入查詢視窗中，然後按一下 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="8c693-251">Copy and paste the following example into the query window and then click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO
```  
  
#### <a name="to-resume-ss_smartbackup-using-powershell"></a><span data-ttu-id="8c693-252">使用 PowerShell 繼續進行 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c693-252">To resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using PowerShell</span></span>  
  
1.  <span data-ttu-id="8c693-253">啟動 PowerShell 執行個體</span><span class="sxs-lookup"><span data-stu-id="8c693-253">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="8c693-254">修改到符合您的設定後，執行下列指令碼。</span><span class="sxs-lookup"><span data-stu-id="8c693-254">Run the following script after you modify it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $True  
    ```  
