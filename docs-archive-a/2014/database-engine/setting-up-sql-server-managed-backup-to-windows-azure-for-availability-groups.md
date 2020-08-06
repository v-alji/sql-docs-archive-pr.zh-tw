---
title: 針對可用性群組設定 SQL Server 受控備份至 Azure |Microsoft Docs
description: 本教學課程說明如何針對參與 Always On 可用性群組的資料庫，設定 SQL Server Managed 備份至 Microsoft Azure。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 0c4553cd-d8e4-4691-963a-4e414cc0f1ba
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebae9f75ac25698582b7f3e4c78c2fb773bd803e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584712"
---
# <a name="setting-up-sql-server-managed-backup-to-azure-for-availability-groups"></a><span data-ttu-id="77f63-103">針對可用性群組設定 SQL Server Managed Backup 到 Azure</span><span class="sxs-lookup"><span data-stu-id="77f63-103">Setting up SQL Server Managed Backup to Azure for Availability Groups</span></span>
  <span data-ttu-id="77f63-104">本主題是設定參與 AlwaysOn 可用性群組之資料庫的[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]之教學課程。</span><span class="sxs-lookup"><span data-stu-id="77f63-104">This topic is a tutorial on configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for databases participating in AlwaysOn Availability Groups.</span></span>  
  
## <a name="availability-group-configurations"></a><span data-ttu-id="77f63-105">可用性群組組態</span><span class="sxs-lookup"><span data-stu-id="77f63-105">Availability Group Configurations</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="77f63-106">可用性群組資料庫支援，不論複本是設定在內部部署或完全在 Azure 上，或是在內部部署與一或多個 Azure 虛擬機器之間的混合式執行。</span><span class="sxs-lookup"><span data-stu-id="77f63-106">is supported for Availability Group databases, whether the replicas are all configured on-premises, or entirely on Azure, or a Hybrid implementation between on-premises and on one or more Azure virtual machines.</span></span> <span data-ttu-id="77f63-107">但是，您可能必須針對一個或多個實作考量以下事項：</span><span class="sxs-lookup"><span data-stu-id="77f63-107">However you might need to consider the following for one or more implementations:</span></span>  
  
-   <span data-ttu-id="77f63-108">記錄備份頻率：記錄備份的頻率會隨著時間和記錄而增加。</span><span class="sxs-lookup"><span data-stu-id="77f63-108">Log Backup Frequency: The frequency of log backup is both time and log growth.</span></span> <span data-ttu-id="77f63-109">例如，系統會每隔兩個小時取得一次記錄備份，除非在這兩個小時內使用的記錄空間為 5 MB 或更多。</span><span class="sxs-lookup"><span data-stu-id="77f63-109">For example, the log backup is taken once every 2 hours unless the log space used within the two hour period is 5 MB or more.</span></span> <span data-ttu-id="77f63-110">這適用於所有實作，不論是內部部署、雲端還是混合式。</span><span class="sxs-lookup"><span data-stu-id="77f63-110">This applies to all implementations, on-premises, cloud, or a Hybrid.</span></span>  
  
-   <span data-ttu-id="77f63-111">網路頻寬：這適用于複本位於不同的實體位置（例如在混合式雲端中），或僅限雲端設定中的不同 Azure 區域的實施。</span><span class="sxs-lookup"><span data-stu-id="77f63-111">Network Bandwidth: This applies to implementations where the replicas are located in different physical locations, like in a hybrid cloud, or across different Azure regions in a cloud only configuration.</span></span> <span data-ttu-id="77f63-112">網路頻寬可能會影響次要複本的延遲，而且如果次要複本設定為同步複寫，這可能會導致主要複本上的記錄增加。</span><span class="sxs-lookup"><span data-stu-id="77f63-112">The network bandwidth can affect the latency of the secondaries and if the secondaries are set to synchronous replication, then this can cause log growth on the primary.</span></span> <span data-ttu-id="77f63-113">如果次要複本設定為同步複寫，次要複本可能會因為網路延遲的緣故而跟不上同步，萬一容錯移轉到次要複本就可能會發生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="77f63-113">If the secondaries are set to synchronous replication, the secondaries may not be able to keep up due to network latency, which can result in data loss in the event of a failover to the secondary replica.</span></span>  
  
### <a name="configuring-ss_smartbackup-for-availability-databases"></a><span data-ttu-id="77f63-114">設定可用性資料庫的[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77f63-114">Configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for Availability Databases.</span></span>  
 <span data-ttu-id="77f63-115">**權限：**</span><span class="sxs-lookup"><span data-stu-id="77f63-115">**Permissions:**</span></span>  
  
-   <span data-ttu-id="77f63-116">需要**db_backupoperator**資料庫角色中的成員資格、具有**ALTER ANY CREDENTIAL**許可權，以及 `EXECUTE` **sp_delete_backuphistory**預存程式的許可權。</span><span class="sxs-lookup"><span data-stu-id="77f63-116">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="77f63-117">需要**smart_admin. fn_get_current_xevent_settings**函數的**SELECT**許可權。</span><span class="sxs-lookup"><span data-stu-id="77f63-117">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="77f63-118">需要 `EXECUTE` smart_admin 的許可權 **。 sp_get_backup_diagnostics**預存程式。</span><span class="sxs-lookup"><span data-stu-id="77f63-118">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="77f63-119">除此之外，因為它會從內部呼叫其他需要此權限的系統物件，所以還需要 `VIEW SERVER STATE` 權限。</span><span class="sxs-lookup"><span data-stu-id="77f63-119">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
-   <span data-ttu-id="77f63-120">需要 `EXECUTE` `smart_admin.sp_set_instance_backup` 和 `smart_admin.sp_backup_master_switch` 預存程式的許可權。</span><span class="sxs-lookup"><span data-stu-id="77f63-120">Requires `EXECUTE` permissions on the `smart_admin.sp_set_instance_backup` and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  
  
 <span data-ttu-id="77f63-121">以下是使用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]設定 AlwaysOn 可用性群組的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="77f63-121">The following are the basic steps to setting up an AlwaysOn Availability Group with [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="77f63-122">本主題稍後將說明詳細的逐步教學課程。</span><span class="sxs-lookup"><span data-stu-id="77f63-122">A detailed step-by step tutorial is described later in this topic.</span></span>  
  
1.  <span data-ttu-id="77f63-123">建立可用性群組之後，請設定慣用的備份複本。</span><span class="sxs-lookup"><span data-stu-id="77f63-123">Once you have created Availability Group, configure the preferred backup replica.</span></span> <span data-ttu-id="77f63-124">也會使用可用性群組的這項設定來決定用於備份的複本。</span><span class="sxs-lookup"><span data-stu-id="77f63-124">This setting for the Availability Group is also used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to determine which replica to use for backup.</span></span> <span data-ttu-id="77f63-125">如需如何設定備份喜好設定的逐步指示，請參閱[在可用性複本上設定備份 &#40;SQL Server&#41;](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="77f63-125">For step by step instructions about how to set up the backup preference, see [Configure Backup on Availability Replicas &#40;SQL Server&#41;](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).</span></span>  <span data-ttu-id="77f63-126">如果您要建立新的 AlwaysOn 可用性群組，請參閱[具有 AlwaysOn 可用性群組 &#40;SQL Server&#41;的消費者入門](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="77f63-126">If you are creating a new AlwaysOn Availability Group, see [Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="77f63-127">設定次要複本的唯讀連接存取。</span><span class="sxs-lookup"><span data-stu-id="77f63-127">Configure read only connection access to the secondary replicas.</span></span> <span data-ttu-id="77f63-128">如需如何設定唯讀存取的逐步指示，請參閱[設定可用性複本上的唯讀存取 &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="77f63-128">For step by step instructions about how to configure read only access, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)</span></span>  
  
3.  <span data-ttu-id="77f63-129">指定備份複本。</span><span class="sxs-lookup"><span data-stu-id="77f63-129">Specify Backup replica.</span></span> <span data-ttu-id="77f63-130">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]會使用慣用的備份複本設定來決定用於排程備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="77f63-130">The preferred backup replica setting is used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to determine which database to use for scheduling backups from..</span></span>  <span data-ttu-id="77f63-131">若要判斷目前的複本是否為慣用的備份複本，請使用[fn_hadr_backup_is_preferred_replica &#40;transact-sql&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)函數。</span><span class="sxs-lookup"><span data-stu-id="77f63-131">To determine whether the current replica is the preferred backup replica, use the [sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function.</span></span>  
  
4.  <span data-ttu-id="77f63-132">在每個複本上 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，使用**智慧型-admin. sp_set_db_backup**預存程式來執行資料庫的設定。</span><span class="sxs-lookup"><span data-stu-id="77f63-132">On each replica run [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration for the database using the **smart-admin.sp_set_db_backup** stored procedure.</span></span>  
  
     <span data-ttu-id="77f63-133">\*\* [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 容錯移轉後的行為：\*\* [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 將會繼續運作，並在容錯移轉事件之後維護備份副本和復原能力。</span><span class="sxs-lookup"><span data-stu-id="77f63-133">**[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] behavior after a failover:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will continue to work and maintain backup copies and recoverability after a failover event.</span></span> <span data-ttu-id="77f63-134">在容錯移轉之後，不需要採取特定的動作。</span><span class="sxs-lookup"><span data-stu-id="77f63-134">No specific action is required after a failover.</span></span>  
  
#### <a name="considerations-and-requirements"></a><span data-ttu-id="77f63-135">考量和需求：</span><span class="sxs-lookup"><span data-stu-id="77f63-135">Considerations and Requirements:</span></span>  
 <span data-ttu-id="77f63-136">針對參與 AlwaysOn 可用性群組的資料庫設定[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]需要進行特定考量並符合特定需求。</span><span class="sxs-lookup"><span data-stu-id="77f63-136">Configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for databases participating in AlwaysOn Availability Group requires specific considerations and requirements.</span></span> <span data-ttu-id="77f63-137">以下是考量與需求清單：</span><span class="sxs-lookup"><span data-stu-id="77f63-137">Following is a list of considerations and requirements:</span></span>  
  
-   <span data-ttu-id="77f63-138">參與相同可用性群組之所有 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 節點上的所有資料庫，都應該具有相同的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]組態設定。</span><span class="sxs-lookup"><span data-stu-id="77f63-138">The [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration settings should be the same for all the databases on all the nodes of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] participating in the same Availability Group.</span></span> <span data-ttu-id="77f63-139">您可以在資料庫層級針對主要及所有複本設定相同的[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]組態，或在參與可用性群組的所有節點上設定相同的預設[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]設定，來達成此目的。</span><span class="sxs-lookup"><span data-stu-id="77f63-139">You can achieve this either by setting  the same [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configurations for the primary and all the replicas at the database level, or by setting the same default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings on all the nodes participating in the Availability Groups.</span></span> <span data-ttu-id="77f63-140">建議在資料庫設定[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，因為在資料庫層級設定[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，可讓您將資料庫與變更的設定，與會影響執行個體上所有其他資料庫的預設值相隔開。</span><span class="sxs-lookup"><span data-stu-id="77f63-140">We recommend setting [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database because configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level lets you isolate the settings to the databases and changes to default settings affect all other databases on the instance.</span></span>  
  
-   <span data-ttu-id="77f63-141">指定備份複本。</span><span class="sxs-lookup"><span data-stu-id="77f63-141">Specify Backup replica.</span></span> <span data-ttu-id="77f63-142">會利用慣用的備份複本，排定備份時程。</span><span class="sxs-lookup"><span data-stu-id="77f63-142">The preferred backup replica setting is used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to schedule the backups.</span></span> <span data-ttu-id="77f63-143">若要判斷目前的複本是否為慣用的備份複本，請使用[fn_hadr_backup_is_preferred_replica &#40;transact-sql&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)函數。</span><span class="sxs-lookup"><span data-stu-id="77f63-143">To determine whether the current replica is the preferred backup replica, use the [sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function.</span></span>  
  
-   <span data-ttu-id="77f63-144">如果將次要複本設定為慣用的複本，請將此複本設定為至少具有唯讀連接存取。</span><span class="sxs-lookup"><span data-stu-id="77f63-144">If the secondary replica is configured as the preferred replica, it should be configured to have at least read only connection access.</span></span> <span data-ttu-id="77f63-145">不支援無法對次要資料庫進行連接存取的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="77f63-145">Availability groups that have no connection access to secondary databases are not supported.</span></span>  <span data-ttu-id="77f63-146">如需詳細資訊，請參閱 [設定可用性複本上的唯讀存取 &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="77f63-146">For more information, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>  
  
-   <span data-ttu-id="77f63-147">如果在設定可用性群組之後設定[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]會嘗試複製以此可用性群組為基礎的所有現有備份，並複製到儲存體容器。</span><span class="sxs-lookup"><span data-stu-id="77f63-147">If you are configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] after you configure the Availability Group, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will attempt to copy any existing backups based and copy them over to the storage container.</span></span>  <span data-ttu-id="77f63-148">如果[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]找不到或無法存取現有的備份，則會排程進行完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="77f63-148">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is unable to find or access existing backups, it will schedule a full database backup.</span></span> <span data-ttu-id="77f63-149">這樣做的原因主要是為了最佳化可用性群組資料庫的備份作業。</span><span class="sxs-lookup"><span data-stu-id="77f63-149">This is done specifically to optimize the backup operations for Availability Group databases.</span></span>  
  
-   <span data-ttu-id="77f63-150">如果您要建立新的可用性資料庫，而且不打算將實例層級設定套用至資料庫，您可以考慮停用實例層級設定。</span><span class="sxs-lookup"><span data-stu-id="77f63-150">You may want to consider disabling the instance level settings if you are creating a new availability database, and you don't intend to apply the instance level settings to the database</span></span>  
  
-   <span data-ttu-id="77f63-151">當使用加密時，請針對所有複本使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="77f63-151">When using encryption, use the same certificate on all the replicas.</span></span> <span data-ttu-id="77f63-152">這樣萬一容錯移轉或還原到不同的複本時，有助於進行持續和不中斷的備份作業。</span><span class="sxs-lookup"><span data-stu-id="77f63-152">This facilitates continued and uninterrupted backup operations in the event of a failover or restores to a different replica.</span></span>  
  
#### <a name="enable-and-configure-ss_smartbackup-for-an-availability-database"></a><span data-ttu-id="77f63-153">啟用及設定可用性資料庫的[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77f63-153">Enable and Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for an Availability Database</span></span>  
 <span data-ttu-id="77f63-154">此教學課程說明為電腦 Node1 和 Node2 上資料庫 (AGTestDB) 啟用及設定[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]的步驟，後面接著啟用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]健康情況之監視功能的步驟。</span><span class="sxs-lookup"><span data-stu-id="77f63-154">This tutorial describes the steps to enable and configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database (AGTestDB) on computers Node1 and Node2, followed by steps to enable monitoring the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
1.  <span data-ttu-id="77f63-155">**建立 Azure 儲存體帳戶：** 這些備份會儲存在 Azure Blob 儲存體服務中。</span><span class="sxs-lookup"><span data-stu-id="77f63-155">**Create an Azure storage account:** The backups are stored in the Azure Blob storage service.</span></span> <span data-ttu-id="77f63-156">如果您還沒有 Azure 儲存體帳戶，您必須先建立它。</span><span class="sxs-lookup"><span data-stu-id="77f63-156">You must first create an Azure storage account, if you do not already have one.</span></span> <span data-ttu-id="77f63-157">如需詳細資訊，請參閱[建立 Azure 儲存體帳戶](https://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/)。</span><span class="sxs-lookup"><span data-stu-id="77f63-157">For more information, see [Creating an Azure Storage Account](https://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/).</span></span> <span data-ttu-id="77f63-158">記下儲存體帳戶的儲存體帳戶名稱、存取金鑰和 URL。</span><span class="sxs-lookup"><span data-stu-id="77f63-158">Make a note of the storage account name, access keys, and URL of the storage account.</span></span> <span data-ttu-id="77f63-159">儲存體帳戶名稱和存取金鑰資訊可用來建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="77f63-159">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="77f63-160">會在備份作業期間使用 SQL 認證來驗證儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="77f63-160">The SQL Credential is used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] during backup operations to authenticate to the storage account.</span></span>  
  
2.  <span data-ttu-id="77f63-161">**建立 SQL 認證：** 使用儲存體帳戶的名稱做為身分識別，並使用儲存體存取金鑰做為密碼，以建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="77f63-161">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="77f63-162">**確認 SQL Server Agent 服務已啟動且在執行中：** 如果目前尚未執行 SQL Server Agent，請加以啟動。</span><span class="sxs-lookup"><span data-stu-id="77f63-162">**Ensure SQL Server Agent service is Started and Running:** Start SQL Server Agent if it is not currently running.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] <span data-ttu-id="77f63-163">需要在執行個體上執行 SQL Server Agent，才能執行備份作業。</span><span class="sxs-lookup"><span data-stu-id="77f63-163">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="77f63-164">您可能需要將 SQL Agent 設定為自動執行，以確保能定期執行備份作業。</span><span class="sxs-lookup"><span data-stu-id="77f63-164">You may want to set SQL Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="77f63-165">**決定保留期限：** 決定您想要用於備份檔案的保留期限。</span><span class="sxs-lookup"><span data-stu-id="77f63-165">**Determine the retention period:** Determine the retention period that you want for the backup files.</span></span> <span data-ttu-id="77f63-166">保留週期的指定單位為天，範圍從 1 到 30。</span><span class="sxs-lookup"><span data-stu-id="77f63-166">The retention period is specified in days and can range from 1 to 30.</span></span> <span data-ttu-id="77f63-167">保留週期可決定資料庫的復原能力時間範圍。</span><span class="sxs-lookup"><span data-stu-id="77f63-167">The retention period determines the recoverability time frame for the database.</span></span>  
  
5.  <span data-ttu-id="77f63-168">**建立要在備份期間用於加密的憑證或非對稱金鑰：** 在第一個節點節點1上建立憑證，然後使用備份憑證將它匯出至檔案[&#40;transact-sql&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="77f63-168">**Create a Certificate or Asymmetric key to use for encryption during back up:** Create the certificate on the first node Node1, and then export it to a file using [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)..</span></span> <span data-ttu-id="77f63-169">在 Node2 上，使用從 Node1 匯出的檔案建立憑證。</span><span class="sxs-lookup"><span data-stu-id="77f63-169">On Node 2, create a certificate using the file exported from Node 1 .</span></span> <span data-ttu-id="77f63-170">如需從檔案建立憑證的詳細資訊，請參閱[CREATE certificate &#40;transact-sql&#41;](/sql/t-sql/statements/create-certificate-transact-sql)中的範例。</span><span class="sxs-lookup"><span data-stu-id="77f63-170">For more information on creating a certificate from a file, see the example in [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
6.  <span data-ttu-id="77f63-171">**啟用和設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 節點1上的 AGTestDB：** Start SQL Server Management Studio 並連接至已安裝可用性資料庫之節點上的實例。</span><span class="sxs-lookup"><span data-stu-id="77f63-171">**Enable and configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for AGTestDB on Node1:** Start SQL Server Management Studio  and connect to the instance on Node1 where the availability database  is installed.</span></span> <span data-ttu-id="77f63-172">在您根據需求修改資料庫名稱、儲存體 URL、SQL 認證和保留週期的值之後，從查詢視窗執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="77f63-172">From the query window run the following statement after you modify the values for the database name, storage URL, SQL Credential and retention period per your requirements:</span></span>  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
    ```  
  
     <span data-ttu-id="77f63-173">如需建立憑證以進行加密的詳細資訊，請參閱[建立加密備份](../relational-databases/backup-restore/create-an-encrypted-backup.md)中的**建立備份憑證**步驟。</span><span class="sxs-lookup"><span data-stu-id="77f63-173">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
7.  <span data-ttu-id="77f63-174">\*\* [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 在節點2上啟用和設定 AGTestDB：\*\* Start SQL Server Management Studio 並連接至已安裝可用性資料庫之節點2上的實例。</span><span class="sxs-lookup"><span data-stu-id="77f63-174">**Enable and configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for AGTestDB on Node2:** Start SQL Server Management Studio and connect to the instance on Node2 where the availability database  is installed.</span></span> <span data-ttu-id="77f63-175">在您根據需求修改資料庫名稱、儲存體 URL、SQL 認證和保留週期的值之後，從查詢視窗執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="77f63-175">From the query window run the following statement after you modify the values for the database name, storage URL, SQL Credential and retention period per your requirements:</span></span>  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
    ```  
  
     [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] <span data-ttu-id="77f63-176">已在您指定的資料庫上啟用。</span><span class="sxs-lookup"><span data-stu-id="77f63-176">is now enabled on the database you specified.</span></span> <span data-ttu-id="77f63-177">資料庫上的備份作業可能需要 15 分鐘才會開始執行。</span><span class="sxs-lookup"><span data-stu-id="77f63-177">It may take up to 15 minutes for the backup operations on the database to start to run.</span></span> <span data-ttu-id="77f63-178">此備份會在慣用的備份複本上進行。</span><span class="sxs-lookup"><span data-stu-id="77f63-178">The backup will occur on the preferred backup replica.</span></span>  
  
8.  <span data-ttu-id="77f63-179">**審查擴充事件的預設設定：** 在用來排程備份的複本上執行下列 transact-sql 語句，以檢查擴充事件設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="77f63-179">**Review Extended Event Default Configuration:**  Review the Extended Event configuration by running the following transact-SQL statement on the replica that [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is using to schedule the backups from.</span></span> <span data-ttu-id="77f63-180">這通常是資料庫所屬之可用性群組的慣用備份複本設定。</span><span class="sxs-lookup"><span data-stu-id="77f63-180">This is usually the preferred backup replica setting for the Availability Group that the database belongs to.</span></span>  
  
    ```sql  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings(); 
    ```  
  
     <span data-ttu-id="77f63-181">預設會顯示已經啟用 Admin、Operational 和 Analytical 通道事件，且無法予以停用。</span><span class="sxs-lookup"><span data-stu-id="77f63-181">You should see that Admin, Operational  and Analytical channel events are enabled by default and cannot be disabled.</span></span> <span data-ttu-id="77f63-182">這應該足以監視需要手動介入的事件。</span><span class="sxs-lookup"><span data-stu-id="77f63-182">This should be sufficient to monitor the events that require manual intervention.</span></span>  <span data-ttu-id="77f63-183">您可以啟用偵錯事件，不過這些通道包含[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]用來偵測及解決問題的資訊和偵錯事件。</span><span class="sxs-lookup"><span data-stu-id="77f63-183">You can enable the debug events, but these channels include informational and debug events that [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] uses to detect issues and solve them.</span></span> <span data-ttu-id="77f63-184">如需詳細資訊，請參閱[監視 SQL Server 受控備份至 Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="77f63-184">For more information, see [Monitor SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
9. <span data-ttu-id="77f63-185">**啟用及設定健全狀態通知：** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的預存程序會建立代理程式作業，以針對可能需要注意的錯誤或警告傳送電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="77f63-185">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span>  <span data-ttu-id="77f63-186">若要接收這類通知，必須啟用 [執行預存程序]，以建立 SQL Server Agent 工作。</span><span class="sxs-lookup"><span data-stu-id="77f63-186">To receive such notifications, you must enable run the stored procedure which creates a SQL Server Agent Job.</span></span> <span data-ttu-id="77f63-187">下列步驟描述啟用及設定電子郵件通知的程序：</span><span class="sxs-lookup"><span data-stu-id="77f63-187">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="77f63-188">如果執行個體上尚未啟用，請設定 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="77f63-188">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="77f63-189">如需詳細資訊，請參閱＜ [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md)＞。</span><span class="sxs-lookup"><span data-stu-id="77f63-189">For more information, see [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="77f63-190">設定 SQL Server Agent 通知使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="77f63-190">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="77f63-191">如需詳細資訊，請參閱 [Configure SQL Server Agent Mail to Use Database Mail](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="77f63-191">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="77f63-192">**啟用電子郵件通知接收備份錯誤和警告：** 從 [查詢] 視窗中，執行下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="77f63-192">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```sql  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email>'  
        ```  
  
         <span data-ttu-id="77f63-193">如需詳細資訊和完整的範例腳本，請參閱[監視 SQL Server 受控備份至 Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="77f63-193">For more information and a full sample script see [Monitor SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
10. <span data-ttu-id="77f63-194">**查看 Azure 儲存體帳戶中的備份檔案：** 從 SQL Server Management Studio 或 Azure 管理入口網站連接到儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="77f63-194">**View backup files in the Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="77f63-195">您會看到裝載設定為使用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的資料庫之 SQL Server 執行個體的容器。</span><span class="sxs-lookup"><span data-stu-id="77f63-195">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="77f63-196">您也會在啟用資料庫之 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的 15 分鐘內，看到資料庫和記錄備份。</span><span class="sxs-lookup"><span data-stu-id="77f63-196">You may also see a database and a log backup within 15 minutes of enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the database.</span></span>  
  
11. <span data-ttu-id="77f63-197">**監視健康狀態：** 您可以透過先前設定的電子郵件通知進行監視，或主動監視記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="77f63-197">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="77f63-198">以下是用於檢視事件的一些 Transact-SQL 陳述式範例：</span><span class="sxs-lookup"><span data-stu-id="77f63-198">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```sql  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event varchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
    ```  
  
    ```sql  
    -- to enable debug events  
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
    ```sql  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
    ```  
  
 <span data-ttu-id="77f63-199">本節所描述的步驟是針對第一次在資料庫上設定 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="77f63-199">The steps described in this section are specifically for configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the first time on the database.</span></span> <span data-ttu-id="77f63-200">您可以使用相同的系統預存程式 smart_admin 來修改現有的設定 **。 sp_set_db_backup**並提供新的值。</span><span class="sxs-lookup"><span data-stu-id="77f63-200">You can modify the existing configurations using the same system stored procedure **smart_admin.sp_set_db_backup** and provide the new values.</span></span> <span data-ttu-id="77f63-201">如需詳細資訊，請參閱[SQL Server 受控備份至 Azure-保留和儲存體設定](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="77f63-201">For more information, see [SQL Server Managed Backup to Azure - Retention and Storage Settings](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
### <a name="considerations-when-removing-a-database-from-alwayson-availability-group-configuration"></a><span data-ttu-id="77f63-202">從 AlwaysOn 可用性群組組態移除資料庫時的考量</span><span class="sxs-lookup"><span data-stu-id="77f63-202">Considerations when Removing a Database from AlwaysOn Availability Group Configuration</span></span>  
 <span data-ttu-id="77f63-203">如果資料庫已從 AlwaysOn 可用性群組設定中移除，而且現在是獨立的資料庫，建議您使用[smart_admin sp_backup_on_demand &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)來進行備份。</span><span class="sxs-lookup"><span data-stu-id="77f63-203">If a database is removed from the AlwaysOn Availability Group configuration and is now a stand-alone database, we recommend doing backup using [smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql).</span></span> <span data-ttu-id="77f63-204">當您以此方式建立資料庫備份時，其會建立新的備份鏈結，且檔案會置於執行個體專屬的容器中，而不是放在可用性容器中 (當資料庫是可用性群組的一部分時，備份會儲存於其中)。</span><span class="sxs-lookup"><span data-stu-id="77f63-204">When you create a database backup  this way, it establishes  a new backup chain and the file will be placed in the instance specific container as opposed to Availability container where the backups were stored when the database was part of Availability Group.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="77f63-205">在此情況下，從可用性群組狀態有所變更前的備份來復原資料庫的能力，則無法保證。</span><span class="sxs-lookup"><span data-stu-id="77f63-205">The recoverability of the database in this scenario from backups previous to the change in the Availability Group status is not guaranteed.</span></span>  
  
