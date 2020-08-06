---
title: 複寫合併代理程式 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Merge Agent, executables
- Merge Agent, parameter reference
- agents [SQL Server replication], Merge Agent
- command prompt [SQL Server replication]
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b3d74dcc6be62ae8a01d911a8404c7bc32fd651
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585901"
---
# <a name="replication-merge-agent"></a><span data-ttu-id="2f856-102">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="2f856-102">Replication Merge Agent</span></span>
  <span data-ttu-id="2f856-103">「複寫合併代理程式」是一個公用程式可執行檔，它會將資料庫資料表中保存的初始快照集套用至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="2f856-103">The Replication Merge Agent is a utility executable that applies the initial snapshot held in the database tables to the Subscribers.</span></span> <span data-ttu-id="2f856-104">此外，它也會合併建立初始快照集之後在「發行者」端發生的累加資料變更，並根據您設定的規則或使用您建立的自訂解析程式來調解衝突。</span><span class="sxs-lookup"><span data-stu-id="2f856-104">It also merges incremental data changes that occurred at the Publisher after the initial snapshot was created, and reconciles conflicts either according to the rules you configure or using a custom resolver you create.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f856-105">您可以使用任何順序來指定參數。</span><span class="sxs-lookup"><span data-stu-id="2f856-105">Parameters can be specified in any order.</span></span> <span data-ttu-id="2f856-106">沒有指定選擇性參數時，系統就會使用本機電腦上預先定義登錄設定的值。</span><span class="sxs-lookup"><span data-stu-id="2f856-106">When optional parameters are not specified, values from predefined registry settings on the local computer are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f856-107">語法</span><span class="sxs-lookup"><span data-stu-id="2f856-107">Syntax</span></span>  
  
```  
  
      replmerg [-?]   
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Publicationpublication-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database  
[-AltSnapshotFolderalt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-DestThreadsnumber_of_destination_threads]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatchdownload_generations_per_batch]  
[-DownloadReadChangesPerBatchdownload_read_changes_per_batch]  
[-DownloadWriteChangesPerBatchdownload_write_changes_per_batch]  
[-DynamicSnapshotLocationdynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]  
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogininternet_login]  
[-InternetPasswordinternet_password]  
[-InternetProxyLogininternet_proxy_login]  
[-InternetProxyPasswordinternet_proxy_password]  
[-InternetProxyServerinternet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeoutinternet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MakeGenerationIntervalmake_generation_interval_seconds]  
[-MaxBcpThreadsnumber_of_threads]  
[-MaxDownloadChangesnumber_of_download_changes]  
[-MaxUploadChangesnumber_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSizepacket_size]   
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOutquery_time_out_seconds]  
[-SrcThreadsnumber_of_source_threads]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatchupload_generations_per_batch]  
[-UploadReadChangesPerBatchupload_read_changes_per_batch]  
[-UploadWriteChangesPerBatchupload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateIntervalvalidate_interval]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f856-108">引數</span><span class="sxs-lookup"><span data-stu-id="2f856-108">Arguments</span></span>  
 <span data-ttu-id="2f856-109">**-?**</span><span class="sxs-lookup"><span data-stu-id="2f856-109">**-?**</span></span>  
 <span data-ttu-id="2f856-110">列印所有可用的參數。</span><span class="sxs-lookup"><span data-stu-id="2f856-110">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="2f856-111">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="2f856-111">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="2f856-112">這是發行者的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-112">Is the name of the Publisher.</span></span> <span data-ttu-id="2f856-113">請針對該伺服器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 *server_name*。</span><span class="sxs-lookup"><span data-stu-id="2f856-113">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="2f856-114">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="2f856-114">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="2f856-115">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="2f856-115">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="2f856-116">這是發行者資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-116">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="2f856-117">**-Publication** _publication_</span><span class="sxs-lookup"><span data-stu-id="2f856-117">**-Publication** _publication_</span></span>  
 <span data-ttu-id="2f856-118">這是發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-118">Is the name of the publication.</span></span> <span data-ttu-id="2f856-119">只有在發行集設定成隨時都有快照供新的訂閱或重新初始化的訂閱使用時，這個參數才有效。</span><span class="sxs-lookup"><span data-stu-id="2f856-119">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="2f856-120">**-Subscriber** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="2f856-120">**-Subscriber** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="2f856-121">這是訂閱者的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-121">Is the name of the Subscriber.</span></span> <span data-ttu-id="2f856-122">請針對該伺服器上的 *預設執行個體指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2f856-122">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="2f856-123">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="2f856-123">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="2f856-124">**-SubscriberDB** _subscriber_database_</span><span class="sxs-lookup"><span data-stu-id="2f856-124">**-SubscriberDB** _subscriber_database_</span></span>  
 <span data-ttu-id="2f856-125">這是訂閱者資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-125">Is the name of the Subscriber database.</span></span>  
  
 <span data-ttu-id="2f856-126">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span><span class="sxs-lookup"><span data-stu-id="2f856-126">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span></span>  
 <span data-ttu-id="2f856-127">這是包含訂閱之初始快照集的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="2f856-127">Is the path to the folder that contains the initial snapshot for a subscription.</span></span>  
  
 <span data-ttu-id="2f856-128">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="2f856-128">**-Continuous**</span></span>  
 <span data-ttu-id="2f856-129">指定代理程式是否會嘗試持續輪詢複寫的交易。</span><span class="sxs-lookup"><span data-stu-id="2f856-129">Specifies whether the agent attempts to poll replicated transactions continually.</span></span> <span data-ttu-id="2f856-130">如果您指定了這個參數，代理程式就會以輪詢間隔輪詢來源的複寫交易，即使沒有任何交易暫止也一樣。</span><span class="sxs-lookup"><span data-stu-id="2f856-130">If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="2f856-131">**-DestThreads** _number_of_destination_threads_</span><span class="sxs-lookup"><span data-stu-id="2f856-131">**-DestThreads** _number_of_destination_threads_</span></span>  
 <span data-ttu-id="2f856-132">指定合併代理程式在目的地套用變更所用的目的地執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-132">Specifies the number of destination threads that the Merge Agent uses to apply changes at the destination.</span></span> <span data-ttu-id="2f856-133">在上傳期間，目的地是發行者，而在下載期間，目的地則是訂閱者。</span><span class="sxs-lookup"><span data-stu-id="2f856-133">The destination is the Publisher during upload and the Subscriber during download.</span></span> <span data-ttu-id="2f856-134">預設值為 4。</span><span class="sxs-lookup"><span data-stu-id="2f856-134">The default is 4.</span></span>  
  
 <span data-ttu-id="2f856-135">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="2f856-135">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="2f856-136">這是代理程式定義檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="2f856-136">Is the path of the agent definition file.</span></span> <span data-ttu-id="2f856-137">代理程式定義檔包含代理程式的命令提示字元引數。</span><span class="sxs-lookup"><span data-stu-id="2f856-137">An agent definition file contains command prompt arguments for the agent.</span></span> <span data-ttu-id="2f856-138">此檔案的內容會剖析為可執行檔。</span><span class="sxs-lookup"><span data-stu-id="2f856-138">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="2f856-139">請使用雙引號 (") 來指定包含任意字元的引數值。</span><span class="sxs-lookup"><span data-stu-id="2f856-139">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="2f856-140">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="2f856-140">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="2f856-141">這是散發者的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-141">Is the Distributor name.</span></span> <span data-ttu-id="2f856-142">請針對該伺服器上的 *預設執行個體指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2f856-142">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="2f856-143">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="2f856-143">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="2f856-144">若為散發者 (發送) 散發，此名稱就會預設為本機電腦上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-144">For Distributor (push) distribution, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="2f856-145">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="2f856-145">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="2f856-146">這是散發者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-146">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="2f856-147">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="2f856-147">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="2f856-148">這是散發者密碼。</span><span class="sxs-lookup"><span data-stu-id="2f856-148">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="2f856-149">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-149">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="2f856-150">指定散發者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="2f856-150">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="2f856-151">值為 **0** 表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證模式 (預設值)，而值為 **1** 則表示 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="2f856-151">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="2f856-152">**-DownloadGenerationsPerBatch** _download_generations_per_batch_</span><span class="sxs-lookup"><span data-stu-id="2f856-152">**-DownloadGenerationsPerBatch** _download_generations_per_batch_</span></span>  
 <span data-ttu-id="2f856-153">這是將變更從發行者下載至訂閱者時，要在單一批次中處理的層代數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-153">Is the number of generations to be processed in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="2f856-154">層代會定義為每個發行項的邏輯變更群組。</span><span class="sxs-lookup"><span data-stu-id="2f856-154">A generation is defined as a logical group of changes per article.</span></span> <span data-ttu-id="2f856-155">可靠通訊連結的預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="2f856-155">The default for a reliable communication link is 100.</span></span> <span data-ttu-id="2f856-156">不可靠通訊連結的預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="2f856-156">The default for an unreliable communication link is 10.</span></span>  
  
 <span data-ttu-id="2f856-157">**-DownloadReadChangesPerBatch** _download_read_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="2f856-157">**-DownloadReadChangesPerBatch** _download_read_changes_per_batch_</span></span>  
 <span data-ttu-id="2f856-158">這是將變更從發行者下載至訂閱者時，要在單一批次中讀取的變更數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-158">Is the number of changes to be read in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="2f856-159">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="2f856-159">The default is 100.</span></span>  
  
 <span data-ttu-id="2f856-160">**-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="2f856-160">**-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_</span></span>  
 <span data-ttu-id="2f856-161">這是將變更從發行者下載至訂閱者時，要在單一批次中套用的變更數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-161">Is the number of changes to be applied in a single batch while downloading changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="2f856-162">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="2f856-162">The default is 100.</span></span>  
  
 <span data-ttu-id="2f856-163">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span><span class="sxs-lookup"><span data-stu-id="2f856-163">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span></span>  
 <span data-ttu-id="2f856-164">這是當發行集使用數化資料列篩選器時，已篩選資料快照集檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="2f856-164">Is the location of the filtered data snapshot files when the publication uses parameterized row filters.</span></span>  
  
 <span data-ttu-id="2f856-165">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="2f856-165">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="2f856-166">這是建立連接時，合併代理程式所使用的安全通訊端層 (SSL) 加密層級。</span><span class="sxs-lookup"><span data-stu-id="2f856-166">Is the level of Secure Sockets Layer (SSL) encryption used by the Merge Agent when making connections.</span></span>  
  
|<span data-ttu-id="2f856-167">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="2f856-167">EncryptionLevel value</span></span>|<span data-ttu-id="2f856-168">描述</span><span class="sxs-lookup"><span data-stu-id="2f856-168">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="2f856-169">**0**</span><span class="sxs-lookup"><span data-stu-id="2f856-169">**0**</span></span>|<span data-ttu-id="2f856-170">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="2f856-170">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="2f856-171">**1**</span><span class="sxs-lookup"><span data-stu-id="2f856-171">**1**</span></span>|<span data-ttu-id="2f856-172">指定要使用 SSL，但是代理程式不會驗證 SSL 伺服器憑證是否由受信任的簽發者簽署。</span><span class="sxs-lookup"><span data-stu-id="2f856-172">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="2f856-173">**2**</span><span class="sxs-lookup"><span data-stu-id="2f856-173">**2**</span></span>|<span data-ttu-id="2f856-174">指定要使用 SSL，而且憑證會經過驗證。</span><span class="sxs-lookup"><span data-stu-id="2f856-174">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="2f856-175">定義的 SSL 憑證必須包含 SQL Server 的完整網域名稱才會有效。</span><span class="sxs-lookup"><span data-stu-id="2f856-175">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="2f856-176">為了讓代理程式能在將 -EncryptionLevel 設定為 2 時成功連線，請在本機 SQL Server 上建立別名。</span><span class="sxs-lookup"><span data-stu-id="2f856-176">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="2f856-177">'Alias Name' 參數應為伺服器名稱，且應將 'Server' 參數設為 SQL Server 的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-177">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="2f856-178">如需詳細資訊，請參閱[SQL Server 複寫安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="2f856-178">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="2f856-179">**-ExchangeType** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="2f856-179">**-ExchangeType** [ **1**| **2**| **3**]</span></span>  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="2f856-180">若要限制上傳，請改用 `@subscriber_upload_options` 的 `sp_addmergearticle`。</span><span class="sxs-lookup"><span data-stu-id="2f856-180">To restrict uploading, use the `@subscriber_upload_options` of `sp_addmergearticle` instead.</span></span>  
  
 <span data-ttu-id="2f856-181">指定同步處理期間資料交換的類型，它可以是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="2f856-181">Specifies the type of data exchange during synchronization, which can be one of the following:</span></span>  
  
|<span data-ttu-id="2f856-182">ExchangeType 值</span><span class="sxs-lookup"><span data-stu-id="2f856-182">ExchangeType value</span></span>|<span data-ttu-id="2f856-183">描述</span><span class="sxs-lookup"><span data-stu-id="2f856-183">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="2f856-184">**1**</span><span class="sxs-lookup"><span data-stu-id="2f856-184">**1**</span></span>|<span data-ttu-id="2f856-185">代理程式應該將資料變更從訂閱者上傳至發行者。</span><span class="sxs-lookup"><span data-stu-id="2f856-185">Agent should upload data changes from the Subscriber to the Publisher.</span></span>|  
|<span data-ttu-id="2f856-186">**2**</span><span class="sxs-lookup"><span data-stu-id="2f856-186">**2**</span></span>|<span data-ttu-id="2f856-187">代理程式應該將資料變更從發行者下載至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="2f856-187">Agent should download data changes from the Publisher to the Subscriber.</span></span>|  
|<span data-ttu-id="2f856-188">**3** (預設)</span><span class="sxs-lookup"><span data-stu-id="2f856-188">**3** (default)</span></span>|<span data-ttu-id="2f856-189">代理程式應該先將資料變更從訂閱者上傳至發行者，然後再將資料變更從發行者下載至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="2f856-189">Agent should first upload data changes from the Subscriber to the Publisher and then download data changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="2f856-190">您必須使用這個選項搭配 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="2f856-190">You must use this option with Web synchronization.</span></span>|  
  
 <span data-ttu-id="2f856-191">僅限下載的發行項可讓您控制發行集中個別發行項的同步處理行為，而且它們可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="2f856-191">Download-only articles enable you to control the synchronization behavior of individual articles in a publication, and they can provide a performance benefit.</span></span> <span data-ttu-id="2f856-192">如需詳細資訊，請參閱[使用僅限下載的發行項最佳化合併式複寫效能](../merge/optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="2f856-192">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](../merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="2f856-193">如果使用 `ExchangeType` 將合併式複寫的上傳和下載階段分成不同的工作階段，您必須先將 `ExchangeType` 設定為 1 來執行合併代理程式，然後將此值設定為 2 再次執行合併代理程式。</span><span class="sxs-lookup"><span data-stu-id="2f856-193">If using `ExchangeType` to separate the upload and download phase of merge replication into separate sessions, you must run the merge agent with `ExchangeType` set to 1 first and then run the merge agent again with the value 2.</span></span> <span data-ttu-id="2f856-194">如果無法使用這兩個參數執行合併代理程式，將會導致中繼資料遭到刪除，而且您將必須重新初始化訂閱 (沒有上傳)。</span><span class="sxs-lookup"><span data-stu-id="2f856-194">Failure to run the merge agent with both parameters will cause metadata to be deleted and require you to reinitialize the subscription (without upload).</span></span>  
  
 <span data-ttu-id="2f856-195">**-FastRowCount** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-195">**-FastRowCount** [**0**|**1**]</span></span>  
 <span data-ttu-id="2f856-196">指定應該針對資料列計數驗證使用哪一種資料列計數計算方法。</span><span class="sxs-lookup"><span data-stu-id="2f856-196">Specifies what type of rowcount calculation method should be used for rowcount validation.</span></span> <span data-ttu-id="2f856-197">值為 **1** (預設值) 表示快速方法。</span><span class="sxs-lookup"><span data-stu-id="2f856-197">A value of **1** (default) indicates the fast method.</span></span> <span data-ttu-id="2f856-198">值為 **0** 則表示完整資料列計數方法。</span><span class="sxs-lookup"><span data-stu-id="2f856-198">A value of **0** indicates the full rowcount method.</span></span>  
  
 <span data-ttu-id="2f856-199">**-FileTransferType** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-199">**-FileTransferType** [**0**|**1**]</span></span>  
 <span data-ttu-id="2f856-200">指定檔案傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="2f856-200">Specifies the file transfer type.</span></span> <span data-ttu-id="2f856-201"> 值為 **0** 表示 UNC (通用命名慣例)，而值為 1 則表示 FTP (檔案傳輸通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="2f856-201">A value of **0** indicates UNC (universal naming convention), and a value of **1** indicates FTP (file transfer protocol).</span></span>  
  
 <span data-ttu-id="2f856-202">**-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]</span><span class="sxs-lookup"><span data-stu-id="2f856-202">**-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]</span></span>  
 <span data-ttu-id="2f856-203">指定合併代理程式應該使用的聚合層級，而且可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="2f856-203">Specifies the level of convergence the Merge Agent should use, and can be one of the following:</span></span>  
  
|<span data-ttu-id="2f856-204">ForceConvergenceLevel 值</span><span class="sxs-lookup"><span data-stu-id="2f856-204">ForceConvergenceLevel value</span></span>|<span data-ttu-id="2f856-205">描述</span><span class="sxs-lookup"><span data-stu-id="2f856-205">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="2f856-206">**0** (預設)</span><span class="sxs-lookup"><span data-stu-id="2f856-206">**0** (default)</span></span>|<span data-ttu-id="2f856-207">預設值。</span><span class="sxs-lookup"><span data-stu-id="2f856-207">Default.</span></span> <span data-ttu-id="2f856-208">執行標準合併，但不進行其他聚合。</span><span class="sxs-lookup"><span data-stu-id="2f856-208">Perform a standard merge without additional convergence.</span></span>|  
|<span data-ttu-id="2f856-209">**1**</span><span class="sxs-lookup"><span data-stu-id="2f856-209">**1**</span></span>|<span data-ttu-id="2f856-210">針對所有層代強制執行聚合。</span><span class="sxs-lookup"><span data-stu-id="2f856-210">Force convergence for all generations.</span></span>|  
|<span data-ttu-id="2f856-211">**2**</span><span class="sxs-lookup"><span data-stu-id="2f856-211">**2**</span></span>|<span data-ttu-id="2f856-212">針對所有層代強制執行聚合並更正損毀的歷程。</span><span class="sxs-lookup"><span data-stu-id="2f856-212">Force convergence for all generations and correct corrupt lineages.</span></span> <span data-ttu-id="2f856-213">指定這個值時，指定應該修正歷程的位置：發行者、訂閱者或發行者與訂閱者兩者。</span><span class="sxs-lookup"><span data-stu-id="2f856-213">When specifying this value, specify where lineages should be corrected: the Publisher, the Subscriber, or both the Publisher and the Subscriber.</span></span>|  
  
 <span data-ttu-id="2f856-214">**-FtpAddress** _ftp_address_</span><span class="sxs-lookup"><span data-stu-id="2f856-214">**-FtpAddress** _ftp_address_</span></span>  
 <span data-ttu-id="2f856-215">這是散發者之 FTP 服務的網路位址。</span><span class="sxs-lookup"><span data-stu-id="2f856-215">Is the network address of the FTP service for the Distributor.</span></span> <span data-ttu-id="2f856-216">沒有指定這個參數時，系統就會使用 **Distributor** 。</span><span class="sxs-lookup"><span data-stu-id="2f856-216">When not specified, **Distributor** is used.</span></span>  
  
 <span data-ttu-id="2f856-217">**-FtpPassword** _ftp_password_</span><span class="sxs-lookup"><span data-stu-id="2f856-217">**-FtpPassword** _ftp_password_</span></span>  
 <span data-ttu-id="2f856-218">這是用來連接到 FTP 服務的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="2f856-218">Is the user password used to connect to the FTP service.</span></span>  
  
 <span data-ttu-id="2f856-219">**-FtpPort** _ftp_port_</span><span class="sxs-lookup"><span data-stu-id="2f856-219">**-FtpPort** _ftp_port_</span></span>  
 <span data-ttu-id="2f856-220">這是散發者的 FTP 服務通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="2f856-220">Is the port number of the FTP service for the Distributor.</span></span> <span data-ttu-id="2f856-221">沒有指定這個參數時，系統就會使用 FTP 服務的預設通訊埠編號 (21)。</span><span class="sxs-lookup"><span data-stu-id="2f856-221">When not specified, the default port number for FTP service (21) is used.</span></span>  
  
 <span data-ttu-id="2f856-222">**-FtpUserName** _ftp_user_name_</span><span class="sxs-lookup"><span data-stu-id="2f856-222">**-FtpUserName** _ftp_user_name_</span></span>  
 <span data-ttu-id="2f856-223">這是用來連接到 FTP 服務的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-223">Is the user name used to connect to the FTP service.</span></span> <span data-ttu-id="2f856-224">沒有指定這個參數時，系統就會使用 anonymous。</span><span class="sxs-lookup"><span data-stu-id="2f856-224">When not specified, anonymous is used.</span></span>  
  
 <span data-ttu-id="2f856-225">**-HistoryVerboseLevel** [**1**|**2**|**3**]</span><span class="sxs-lookup"><span data-stu-id="2f856-225">**-HistoryVerboseLevel** [**1**|**2**|**3**]</span></span>  
 <span data-ttu-id="2f856-226">指定在合併作業期間記錄的記錄量。</span><span class="sxs-lookup"><span data-stu-id="2f856-226">Specifies the amount of history logged during a merge operation.</span></span> <span data-ttu-id="2f856-227">您可以透過選取 **1**，盡量減少記錄作業對效能造成的影響。</span><span class="sxs-lookup"><span data-stu-id="2f856-227">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="2f856-228">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="2f856-228">HistoryVerboseLevel value</span></span>|<span data-ttu-id="2f856-229">描述</span><span class="sxs-lookup"><span data-stu-id="2f856-229">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="2f856-230">**0**</span><span class="sxs-lookup"><span data-stu-id="2f856-230">**0**</span></span>|<span data-ttu-id="2f856-231">記錄最終代理程式狀態訊息、最終工作階段詳細資料，以及任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="2f856-231">Log the final agent status message, final session details, and any errors.</span></span>|  
|<span data-ttu-id="2f856-232">**1**</span><span class="sxs-lookup"><span data-stu-id="2f856-232">**1**</span></span>|<span data-ttu-id="2f856-233">除了最終代理程式狀態訊息、最終工作階段詳細資料以及任何錯誤以外，記錄每個工作階段狀態的累加工作階段詳細資料，包括完成百分比。</span><span class="sxs-lookup"><span data-stu-id="2f856-233">Log incremental session details at each session status, including percent complete, in addition to the final agent status message, final session details, and any errors.</span></span>|  
|<span data-ttu-id="2f856-234">**2**</span><span class="sxs-lookup"><span data-stu-id="2f856-234">**2**</span></span>|<span data-ttu-id="2f856-235">預設值。</span><span class="sxs-lookup"><span data-stu-id="2f856-235">Default.</span></span> <span data-ttu-id="2f856-236">除了最終代理程式狀態訊息、最終工作階段詳細資料以及任何錯誤以外，記錄每個工作階段狀態的累加工作階段詳細資料和發行項層級工作階段詳細資料，包括完成百分比。</span><span class="sxs-lookup"><span data-stu-id="2f856-236">Log both incremental session details at each session status and article level session details, including percent complete, in addition to the final agent status message, final session details, and any errors.</span></span> <span data-ttu-id="2f856-237">此外，系統也會記錄代理程式狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="2f856-237">Agent status messages are also logged.</span></span>|  
|<span data-ttu-id="2f856-238">**3**</span><span class="sxs-lookup"><span data-stu-id="2f856-238">**3**</span></span>|<span data-ttu-id="2f856-239">與 **-HistoryVerboseLevel** = **2**相同，但是系統會記錄更多代理程式進度訊息。</span><span class="sxs-lookup"><span data-stu-id="2f856-239">The same as **-HistoryVerboseLevel** = **2**, except that more agent progress messages are logged.</span></span>|  
  
 <span data-ttu-id="2f856-240">**-Hostname** _host_name_</span><span class="sxs-lookup"><span data-stu-id="2f856-240">**-Hostname** _host_name_</span></span>  
 <span data-ttu-id="2f856-241">這是本機電腦的網路名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-241">Is the network name of the local computer.</span></span> <span data-ttu-id="2f856-242">預設值為本機電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-242">The default is the local computer name.</span></span>  
  
 <span data-ttu-id="2f856-243">**-InteractiveResolution** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-243">**-InteractiveResolution** [**0**|**1**]</span></span>  
 <span data-ttu-id="2f856-244">指定在同步處理期間發生衝突時，是否要使用互動式衝突解決方案。</span><span class="sxs-lookup"><span data-stu-id="2f856-244">Specifies whether interactive conflict resolution is used when a conflict occurs during synchronization.</span></span> <span data-ttu-id="2f856-245">預設值為 **0**，表示不使用互動式衝突解決方案。</span><span class="sxs-lookup"><span data-stu-id="2f856-245">The default is **0**, indicating that interactive conflict resolution is not used.</span></span>  
  
 <span data-ttu-id="2f856-246">**-InternetLogin** _internet_login_</span><span class="sxs-lookup"><span data-stu-id="2f856-246">**-InternetLogin** _internet_login_</span></span>  
 <span data-ttu-id="2f856-247">指定連接至需要驗證之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Listener ISAPI DLL 時使用的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-247">Specifies the login name used when connecting to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL that requires authentication.</span></span>  
  
 <span data-ttu-id="2f856-248">**-InternetPassword** _internet_password_</span><span class="sxs-lookup"><span data-stu-id="2f856-248">**-InternetPassword** _internet_password_</span></span>  
 <span data-ttu-id="2f856-249">指定連接至需要驗證之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Listener ISAPI DLL 時使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="2f856-249">Specifies the password used when connecting to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL that requires authentication.</span></span>  
  
 <span data-ttu-id="2f856-250">**-InternetProxyLogin**  *internet_proxy_login*</span><span class="sxs-lookup"><span data-stu-id="2f856-250">**-InternetProxyLogin**  *internet_proxy_login*</span></span>  
 <span data-ttu-id="2f856-251">指定連接至需要驗證之 Proxy 伺服器 (定義於 *internet_proxy_server*) 時使用的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-251">Specifies the login name used when connecting to a proxy server, defined in *internet_proxy_server*, that requires authentication.</span></span>  
  
 <span data-ttu-id="2f856-252">**-InternetProxyPassword**  *internet_proxy_password*</span><span class="sxs-lookup"><span data-stu-id="2f856-252">**-InternetProxyPassword**  *internet_proxy_password*</span></span>  
 <span data-ttu-id="2f856-253">指定連接至需要驗證之 Proxy 伺服器 (定義於 *internet_proxy_server*) 時使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="2f856-253">Specifies the password used when connecting to a proxy server, defined in *internet_proxy_server*, that requires authentication.</span></span>  
  
 <span data-ttu-id="2f856-254">**-InternetProxyServer**  *internet_proxy_server*</span><span class="sxs-lookup"><span data-stu-id="2f856-254">**-InternetProxyServer**  *internet_proxy_server*</span></span>  
 <span data-ttu-id="2f856-255">指定要在存取 *internet_url*中指定之 HTTP 資源時使用的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f856-255">Specifies the proxy server to use when accessing the HTTP resource specified in *internet_url*.</span></span>  
  
 <span data-ttu-id="2f856-256">**-InternetSecurityMode** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-256">**-InternetSecurityMode** [**0**|**1**]</span></span>  
 <span data-ttu-id="2f856-257">指定在 Web 同步處理期間，連接至 Web 伺服器時使用的 IIS 安全性模式。</span><span class="sxs-lookup"><span data-stu-id="2f856-257">Specifies the IIS security mode used when connecting to the Web server during Web synchronization.</span></span> <span data-ttu-id="2f856-258">值為 **0** 表示基本驗證，而值為 **1** 則表示 Windows 整合式驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="2f856-258">A value of **0** indicates Basic Authentication, and a value of **1** indicates Windows Integrated Authentication (default).</span></span>  
  
 <span data-ttu-id="2f856-259">**-InternetTimeout** _internet_timeout_</span><span class="sxs-lookup"><span data-stu-id="2f856-259">**-InternetTimeout** _internet_timeout_</span></span>  
 <span data-ttu-id="2f856-260">這是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Listener ISAPI DLL 的連接逾時之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="2f856-260">Is the number of seconds before a connection to the to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL times out.</span></span>  
  
 <span data-ttu-id="2f856-261">**-InternetURL** _internet_url_</span><span class="sxs-lookup"><span data-stu-id="2f856-261">**-InternetURL** _internet_url_</span></span>  
 <span data-ttu-id="2f856-262">指定用來連接至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Listener ISAPI DLL 的 URL。</span><span class="sxs-lookup"><span data-stu-id="2f856-262">Specifies the URL used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication listener ISAPI DLL.</span></span> <span data-ttu-id="2f856-263">您必須指定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="2f856-263">This property must be specified.</span></span>  
  
 <span data-ttu-id="2f856-264">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="2f856-264">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="2f856-265">這是記錄執行緒檢查是否有任何現有的連接正在等候伺服器回應之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="2f856-265">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="2f856-266">執行長時間執行的批次時，您可以減少這個值，避免檢查代理程式將合併代理程式標示為有疑問。</span><span class="sxs-lookup"><span data-stu-id="2f856-266">This value can be decreased to avoid having the checkup agent mark the Merge Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="2f856-267">預設值是 **300** 秒。</span><span class="sxs-lookup"><span data-stu-id="2f856-267">The default is **300** seconds.</span></span>  
  
 <span data-ttu-id="2f856-268">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="2f856-268">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="2f856-269">這是登入逾時之前的秒數。 預設值為 15 秒。</span><span class="sxs-lookup"><span data-stu-id="2f856-269">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="2f856-270">**-MakeGenerationInterval** _make_generation_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="2f856-270">**-MakeGenerationInterval** _make_generation_interval_seconds_</span></span>  
 <span data-ttu-id="2f856-271">這是建立層代或變更批次之間等待的秒數，以便下載到用戶端。</span><span class="sxs-lookup"><span data-stu-id="2f856-271">Is the number of seconds to wait between creating generations, or batches of changes, to download to the client.</span></span> <span data-ttu-id="2f856-272">預設值為 **1** 秒。</span><span class="sxs-lookup"><span data-stu-id="2f856-272">The default is **1** second.</span></span>  
  
 <span data-ttu-id="2f856-273">Makegeneration 是準備將發行者變更下載到訂閱者的程序，而且在它下載期間可能是效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="2f856-273">Makegeneration is the process that prepares Publisher changes to be downloaded to Subscribers, and it can be a performance bottleneck during downloads.</span></span> <span data-ttu-id="2f856-274">如果 makegeneration 程序已經在 **-MakeGenerationInterval**指定的間隔內執行，則會略過目前同步處理工作階段的程序。</span><span class="sxs-lookup"><span data-stu-id="2f856-274">If the makegeneration process already ran within the interval specified by **-MakeGenerationInterval**, the process is skipped for the current synchronization session.</span></span> <span data-ttu-id="2f856-275">這有助於進行並行同步處理，而且在訂閱者不想要下載變更時特別實用。</span><span class="sxs-lookup"><span data-stu-id="2f856-275">This can benefit synchronization concurrency and is especially helpful if Subscribers do not expect to download changes.</span></span>  
  
 <span data-ttu-id="2f856-276">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="2f856-276">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="2f856-277">指定可用平行方式執行的大量複製作業數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-277">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="2f856-278">同時存在之執行緒和 ODBC 連接的最大數目是 **MaxBcpThreads** 或發行集資料庫之系統資料表 **sysmergeschemachange** 中顯示的大量複製要求數目的較小者。</span><span class="sxs-lookup"><span data-stu-id="2f856-278">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the system table **sysmergeschemachange** in the publication database.</span></span> <span data-ttu-id="2f856-279">**MaxBcpThreads** 必須具有大於 0 的值而且沒有硬式編碼的上限。</span><span class="sxs-lookup"><span data-stu-id="2f856-279">**MaxBcpThreads** must have a value greater than 0 and has no hard-coded upper limit.</span></span> <span data-ttu-id="2f856-280">預設為 **1**。</span><span class="sxs-lookup"><span data-stu-id="2f856-280">The default is **1**.</span></span>  
  
 <span data-ttu-id="2f856-281">**-MaxDownloadChanges** _number_of_download_changes_</span><span class="sxs-lookup"><span data-stu-id="2f856-281">**-MaxDownloadChanges** _number_of_download_changes_</span></span>  
 <span data-ttu-id="2f856-282">指定應該從發行者下載至訂閱者的最大變更資料列數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-282">Specifies the maximum number of changed rows that should be downloaded from the Publisher to the Subscriber.</span></span> <span data-ttu-id="2f856-283">所下載的資料列數目可能會高於指定的最大值，因為：系統會處理完整的層代，而且平行目的地執行緒可能會執行，其中每個執行緒在第一次傳遞時至少會處理 100 項變更。</span><span class="sxs-lookup"><span data-stu-id="2f856-283">The number of rows downloaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass.</span></span> <span data-ttu-id="2f856-284">根據預設，系統會傳送準備下載的所有變更。</span><span class="sxs-lookup"><span data-stu-id="2f856-284">By default all changes that are ready to be downloaded are sent.</span></span>  
  
 <span data-ttu-id="2f856-285">**-MaxUploadChanges** _number_of_upload_changes_</span><span class="sxs-lookup"><span data-stu-id="2f856-285">**-MaxUploadChanges** _number_of_upload_changes_</span></span>  
 <span data-ttu-id="2f856-286">指定應該從訂閱者上傳至發行者的最大變更資料列數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-286">Specifies the maximum number of changed rows that should be uploaded from the Subscriber to the Publisher.</span></span> <span data-ttu-id="2f856-287">所上傳的資料列數目可能會高於指定的最大值，因為：系統會處理完整的層代，而且平行目的地執行緒可能會執行，其中每個執行緒在第一次傳遞時至少會處理 100 項變更。</span><span class="sxs-lookup"><span data-stu-id="2f856-287">The number of rows uploaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass.</span></span> <span data-ttu-id="2f856-288">根據預設，系統會傳送準備上傳的所有變更。</span><span class="sxs-lookup"><span data-stu-id="2f856-288">By default all changes that are ready to be uploaded are sent.</span></span>  
  
 <span data-ttu-id="2f856-289">**-MetadataRetentionCleanup** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-289">**-MetadataRetentionCleanup** [**0**|**1**]</span></span>  
 <span data-ttu-id="2f856-290">指定是否應該根據發行集保留週期，從 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)、 [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)和 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) 中移除中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2f856-290">Specifies if metadata is removed from [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql), and [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) based on the publication retention period.</span></span> <span data-ttu-id="2f856-291">預設值為 **1**，表示應該進行清除。</span><span class="sxs-lookup"><span data-stu-id="2f856-291">The default is **1**, indicating that cleanup should occur.</span></span> <span data-ttu-id="2f856-292">值為 **0** 則表示不應該自動進行清除。</span><span class="sxs-lookup"><span data-stu-id="2f856-292">A value of **0** indicates that cleanup should not occur automatically.</span></span>  
  
 <span data-ttu-id="2f856-293">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="2f856-293">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="2f856-294">這是代理程式輸出檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="2f856-294">Is the path of the agent output file.</span></span> <span data-ttu-id="2f856-295">如果未提供檔案名稱，輸出將傳送至主控台。</span><span class="sxs-lookup"><span data-stu-id="2f856-295">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="2f856-296">如果指定的檔案名稱存在，輸出就會附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="2f856-296">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="2f856-297">**-OutputVerboseLevel** [**0**|**1**|**2**]</span><span class="sxs-lookup"><span data-stu-id="2f856-297">**-OutputVerboseLevel** [**0**|**1**|**2**]</span></span>  
 <span data-ttu-id="2f856-298">指定輸出是否應該詳細。</span><span class="sxs-lookup"><span data-stu-id="2f856-298">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="2f856-299">如果詳細資訊層級為 0，系統就只會列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2f856-299">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="2f856-300">如果詳細資訊層級為 **1**，系統就會列印所有進度報表訊息。</span><span class="sxs-lookup"><span data-stu-id="2f856-300">If the verbose level is **1**, all of the progress report messages are printed.</span></span> <span data-ttu-id="2f856-301">如果詳細資訊層級為 2 (預設值)，系統就會列印所有錯誤訊息和進度報表訊息 (可用於偵錯)。</span><span class="sxs-lookup"><span data-stu-id="2f856-301">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="2f856-302">**-ParallelUploadDownload** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-302">**-ParallelUploadDownload** [**0**|**1**]</span></span>  
 <span data-ttu-id="2f856-303">指定合併代理程式是否應該以平行方式處理上傳至發行者的變更以及下載至訂閱者的變更，而且這個參數在具有高網路頻寬的高容量環境中很有用。</span><span class="sxs-lookup"><span data-stu-id="2f856-303">Specifies whether the Merge Agent should process in parallel the changes uploaded to the Publisher and those downloaded to the Subscriber, which is useful in high volume environments with high network bandwidth.</span></span> <span data-ttu-id="2f856-304">如果 **ParallelUploadDownload** 是 **1**，就會啟用平行處理。</span><span class="sxs-lookup"><span data-stu-id="2f856-304">If **ParallelUploadDownload** is **1**, then parallel processing is enabled.</span></span>  
  
 <span data-ttu-id="2f856-305">**-PacketSize**</span><span class="sxs-lookup"><span data-stu-id="2f856-305">**-PacketSize**</span></span>  
 <span data-ttu-id="2f856-306">這是封包大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="2f856-306">Is the packet size, in bytes.</span></span> <span data-ttu-id="2f856-307">預設值是 4096 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="2f856-307">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="2f856-308">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="2f856-308">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="2f856-309">這是針對資料變更查詢發行者或訂閱者的頻率 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="2f856-309">Is how often, in seconds, the Publisher or Subscriber is queried for data changes.</span></span> <span data-ttu-id="2f856-310">預設值是 60 秒。</span><span class="sxs-lookup"><span data-stu-id="2f856-310">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="2f856-311">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="2f856-311">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="2f856-312">指定要用於代理程式參數的代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="2f856-312">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="2f856-313">如果 **ProfileName** 為 NULL，就會停用代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="2f856-313">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="2f856-314">如果沒有指定 **ProfileName** ，就會使用該代理程式類型的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="2f856-314">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="2f856-315">如需資訊，請參閱[複寫代理程式設定檔](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="2f856-315">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="2f856-316">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="2f856-316">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="2f856-317">指定參與具有發行集資料庫之資料庫鏡像工作階段的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉夥伴執行個體。</span><span class="sxs-lookup"><span data-stu-id="2f856-317">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="2f856-318">如需詳細資訊，請參閱 [資料庫鏡像和複寫 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2f856-318">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="2f856-319">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="2f856-319">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="2f856-320">這是發行者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-320">Is the Publisher login name.</span></span> <span data-ttu-id="2f856-321">如果 **PublisherSecurityMode** 是 **0** (代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證)，您就必須指定這個參數。</span><span class="sxs-lookup"><span data-stu-id="2f856-321">If **PublisherSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="2f856-322">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="2f856-322">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="2f856-323">這是發行者密碼。</span><span class="sxs-lookup"><span data-stu-id="2f856-323">Is the Publisher password.</span></span> <span data-ttu-id="2f856-324">如果 **PublisherSecurityMode** 是 **0** (代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證)，您就必須指定這個參數。</span><span class="sxs-lookup"><span data-stu-id="2f856-324">If **PublisherSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="2f856-325">**-PublisherSecurityMode** [**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-325">**-PublisherSecurityMode** [**0**|**1**]</span></span>  
 <span data-ttu-id="2f856-326">指定發行者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="2f856-326">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="2f856-327">值為 **0** 表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證 (預設值)，而值為 **1** 則表示 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="2f856-327">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="2f856-328">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="2f856-328">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="2f856-329">這是查詢逾時之前的秒數。預設為 300 秒。</span><span class="sxs-lookup"><span data-stu-id="2f856-329">Is the number of seconds before the query times out. The default is 300 seconds.</span></span> <span data-ttu-id="2f856-330">此外，當這個值大於 1800 時，合併代理程式也會使用 `QueryTimeout` 的值來決定等候資料分割快照集產生的時間長度。</span><span class="sxs-lookup"><span data-stu-id="2f856-330">The Merge Agent also uses the value of `QueryTimeout` to determine how long to wait for generation of a partitioned snapshot when this value is greater than 1800.</span></span>  
  
 <span data-ttu-id="2f856-331">**-SrcThreads** _number_of_source_threads_</span><span class="sxs-lookup"><span data-stu-id="2f856-331">**-SrcThreads** _number_of_source_threads_</span></span>  
 <span data-ttu-id="2f856-332">指定合併代理程式從來源列舉變更所用的來源執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-332">Specifies the number of source threads that the Merge Agent uses to enumerate changes from the source.</span></span> <span data-ttu-id="2f856-333">在上傳期間，來源是訂閱者，而在下載期間，來源則是發行者。</span><span class="sxs-lookup"><span data-stu-id="2f856-333">The source is the Subscriber during upload and the Publisher during download.</span></span> <span data-ttu-id="2f856-334">預設為 **3**。</span><span class="sxs-lookup"><span data-stu-id="2f856-334">The default is **3**.</span></span>  
  
 <span data-ttu-id="2f856-335">**-StartQueueTimeout** _start_queue_timeout_seconds_</span><span class="sxs-lookup"><span data-stu-id="2f856-335">**-StartQueueTimeout** _start_queue_timeout_seconds_</span></span>  
 <span data-ttu-id="2f856-336">這是當執行中並行合併進程的數目是由 sp_addmergepublication 的屬性所設定的限制時，合併代理程式等待的最大秒數 **@max_concurrent_merge** 。 **sp_addmergepublication**</span><span class="sxs-lookup"><span data-stu-id="2f856-336">Is the maximum number of seconds that the Merge Agent waits when the number of concurrent merge processes running is at the limit set by the **@max_concurrent_merge** property of **sp_addmergepublication**.</span></span> <span data-ttu-id="2f856-337">如果已到達最大秒數而且合併代理程式仍然等候中，它就會結束。</span><span class="sxs-lookup"><span data-stu-id="2f856-337">If the maximum number of seconds is reached and the Merge Agent is still waiting, it will exit.</span></span> <span data-ttu-id="2f856-338">值為 0 表示代理程式會永遠等候，不過您可以取消它。</span><span class="sxs-lookup"><span data-stu-id="2f856-338">A value of 0 means that the agent waits indefinitely, although it can be cancelled.</span></span>  
  
 <span data-ttu-id="2f856-339">**-SubscriberDatabasePath** _subscriber_database_path_</span><span class="sxs-lookup"><span data-stu-id="2f856-339">**-SubscriberDatabasePath** _subscriber_database_path_</span></span>  
 <span data-ttu-id="2f856-340">如果 **SubscriberType** 是 **2** (允許連接至沒有 ODBC 資料來源名稱 (DSN) 的 Jet 資料庫)，這就是 Jet 資料庫 (.mdb 檔) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-340">Is the path to the Jet database (.mdb file) if **SubscriberType** is **2** (allows a connection to a Jet database without an ODBC Data Source Name (DSN)).</span></span>  
  
 <span data-ttu-id="2f856-341">**-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="2f856-341">**-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="2f856-342">指定現有的訂閱者資料庫是否存在。</span><span class="sxs-lookup"><span data-stu-id="2f856-342">Specifies whether there is an existing Subscriber database.</span></span>  
  
|<span data-ttu-id="2f856-343">SubscriberDBAddOption 值</span><span class="sxs-lookup"><span data-stu-id="2f856-343">SubscriberDBAddOption value</span></span>|<span data-ttu-id="2f856-344">描述</span><span class="sxs-lookup"><span data-stu-id="2f856-344">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="2f856-345">**0**</span><span class="sxs-lookup"><span data-stu-id="2f856-345">**0**</span></span>|<span data-ttu-id="2f856-346">使用現有的資料庫 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="2f856-346">Use the existing database (default).</span></span>|  
|<span data-ttu-id="2f856-347">**1**</span><span class="sxs-lookup"><span data-stu-id="2f856-347">**1**</span></span>|<span data-ttu-id="2f856-348">建立新的空白訂閱者資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f856-348">Create a new, empty Subscriber database.</span></span>|  
|<span data-ttu-id="2f856-349">**2**</span><span class="sxs-lookup"><span data-stu-id="2f856-349">**2**</span></span>|<span data-ttu-id="2f856-350">建立新的資料庫並將它附加至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="2f856-350">Create a new database and attach it to the specified file.</span></span>|  
|<span data-ttu-id="2f856-351">**3**</span><span class="sxs-lookup"><span data-stu-id="2f856-351">**3**</span></span>|<span data-ttu-id="2f856-352">建立新的資料庫、附加該資料庫，然後啟用可能存在檔案中的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="2f856-352">Create a new database, attach the database, and enable all subscriptions that might exist at the file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="2f856-353">當您使用 **2** 和 **3**值時，就必須在 **SubscriberDatabasePath** 選項中指定訂閱者的資料庫路徑。</span><span class="sxs-lookup"><span data-stu-id="2f856-353">When you use values **2** and **3**, the database path for the Subscriber must be specified in the **SubscriberDatabasePath** option.</span></span>  
  
 <span data-ttu-id="2f856-354">**-SubscriberLogin** _subscriber_login_</span><span class="sxs-lookup"><span data-stu-id="2f856-354">**-SubscriberLogin** _subscriber_login_</span></span>  
 <span data-ttu-id="2f856-355">這是訂閱者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="2f856-355">Is the Subscriber login name.</span></span> <span data-ttu-id="2f856-356">如果 **SubscriberSecurityMode** 是 **0** (代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證)，您就必須指定這個參數。</span><span class="sxs-lookup"><span data-stu-id="2f856-356">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="2f856-357">**-SubscriberPassword** _subscriber_password_</span><span class="sxs-lookup"><span data-stu-id="2f856-357">**-SubscriberPassword** _subscriber_password_</span></span>  
 <span data-ttu-id="2f856-358">這是訂閱者密碼。</span><span class="sxs-lookup"><span data-stu-id="2f856-358">Is the Subscriber password.</span></span> <span data-ttu-id="2f856-359">如果 **SubscriberSecurityMode** 是 **0** (代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證)，您就必須指定這個參數。</span><span class="sxs-lookup"><span data-stu-id="2f856-359">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="2f856-360">**-SubscriberSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-360">**-SubscriberSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="2f856-361">指定訂閱者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="2f856-361">Specifies the security mode of the Subscriber.</span></span> <span data-ttu-id="2f856-362">值為 **0** 表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證 (預設值)，而值為 **1** 則表示 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="2f856-362">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="2f856-363">**-SubscriberConflictClean** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-363">**-SubscriberConflictClean** [ **0**| **1**]</span></span>  
 <span data-ttu-id="2f856-364">是否要在同步處理過程中清除訂閱者端的衝突資料表。值為 **1** 表示要清除訂閱者端的衝突資料表。</span><span class="sxs-lookup"><span data-stu-id="2f856-364">Is if conflict tables are cleaned-up at the Subscriber during the synchronization process, where a value of **1** indicates that conflict tables at the Subscriber are cleaned-up.</span></span> <span data-ttu-id="2f856-365">這個參數只能用於具有分散式衝突記錄之發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="2f856-365">This parameter is used only for subscriptions to publications with decentralized conflict logging.</span></span>  
  
 <span data-ttu-id="2f856-366">**-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]</span><span class="sxs-lookup"><span data-stu-id="2f856-366">**-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]</span></span>  
 <span data-ttu-id="2f856-367">指定由合併代理程式所使用的訂閱者連接類型。</span><span class="sxs-lookup"><span data-stu-id="2f856-367">Specifies the type of Subscriber connection used by the Merge Agent.</span></span> <span data-ttu-id="2f856-368">只有預設值 **0** 支援這個參數。</span><span class="sxs-lookup"><span data-stu-id="2f856-368">Only the default value of **0** is supported for this parameter.</span></span>  
  
 <span data-ttu-id="2f856-369">**-SubscriptionType**[ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="2f856-369">**-SubscriptionType**[ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="2f856-370">指定散發的訂閱類型。</span><span class="sxs-lookup"><span data-stu-id="2f856-370">Specifies the subscription type for distribution.</span></span> <span data-ttu-id="2f856-371">值為 **0** 表示發送訂閱 (預設值)、值為 **1** 表示提取訂閱，而值為 **2** 則表示匿名訂閱。</span><span class="sxs-lookup"><span data-stu-id="2f856-371">A value of **0** indicates a push subscription (default), a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.</span></span>  
  
 <span data-ttu-id="2f856-372">**-SyncToAlternate** [ **0|1**]</span><span class="sxs-lookup"><span data-stu-id="2f856-372">**-SyncToAlternate** [ **0|1**]</span></span>  
 <span data-ttu-id="2f856-373">指定合併代理程式是否會在訂閱者與替代發行者之間進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="2f856-373">Specifies whether the Merge Agent is synchronizing between a Subscriber and an alternate Publisher.</span></span> <span data-ttu-id="2f856-374">值為 **1** 表示它是替代發行者。</span><span class="sxs-lookup"><span data-stu-id="2f856-374">A value of **1** indicates that it is an alternate Publisher.</span></span> <span data-ttu-id="2f856-375">預設為 **0**。</span><span class="sxs-lookup"><span data-stu-id="2f856-375">The default is **0**.</span></span>  
  
 <span data-ttu-id="2f856-376">**-UploadGenerationsPerBatch** _upload_generations_per_batch_</span><span class="sxs-lookup"><span data-stu-id="2f856-376">**-UploadGenerationsPerBatch** _upload_generations_per_batch_</span></span>  
 <span data-ttu-id="2f856-377">這是將變更從訂閱者上傳至發行者時，要在單一批次中處理的層代數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-377">Is the number of generations to be processed in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="2f856-378">層代會定義為每個發行項的邏輯變更群組。</span><span class="sxs-lookup"><span data-stu-id="2f856-378">A generation is defined as a logical group of changes per article.</span></span> <span data-ttu-id="2f856-379">可靠通訊連結的預設值為 **100**。</span><span class="sxs-lookup"><span data-stu-id="2f856-379">The default for a reliable communication link is **100**.</span></span> <span data-ttu-id="2f856-380">不可靠通訊連結的預設值為 **1**。</span><span class="sxs-lookup"><span data-stu-id="2f856-380">The default for an unreliable communication link is **1**.</span></span>  
  
 <span data-ttu-id="2f856-381">**-UploadReadChangesPerBatch** _upload_read_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="2f856-381">**-UploadReadChangesPerBatch** _upload_read_changes_per_batch_</span></span>  
 <span data-ttu-id="2f856-382">這是將變更從訂閱者上傳至發行者時，要在單一批次中讀取的變更數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-382">Is the number of changes to be read in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="2f856-383">預設為 **100**。</span><span class="sxs-lookup"><span data-stu-id="2f856-383">The default is **100**.</span></span>  
  
 <span data-ttu-id="2f856-384">**-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_</span><span class="sxs-lookup"><span data-stu-id="2f856-384">**-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_</span></span>  
 <span data-ttu-id="2f856-385">這是將變更從訂閱者上傳至發行者時，要在單一批次中套用的變更數目。</span><span class="sxs-lookup"><span data-stu-id="2f856-385">Is the number of changes to be applied in a single batch while uploading changes from the Subscriber to the Publisher.</span></span> <span data-ttu-id="2f856-386">預設為 **100**。</span><span class="sxs-lookup"><span data-stu-id="2f856-386">The default is **100**.</span></span>  
  
 <span data-ttu-id="2f856-387">**-UseInprocLoader**</span><span class="sxs-lookup"><span data-stu-id="2f856-387">**-UseInprocLoader**</span></span>  
 <span data-ttu-id="2f856-388">將快照集檔案套用至訂閱者時，讓合併代理程式使用 BULK INSERT 命令，藉以改善初始快照集的效能。</span><span class="sxs-lookup"><span data-stu-id="2f856-388">Improves the performance of the initial snapshot by causing the Merge Agent to use the BULK INSERT command when applying snapshot files to the Subscriber.</span></span> <span data-ttu-id="2f856-389">這個參數已被取代，因為它與 XML 資料類型不相容。</span><span class="sxs-lookup"><span data-stu-id="2f856-389">This parameter is deprecated because it is not compatible with the XML data type.</span></span> <span data-ttu-id="2f856-390">如果您不複寫 XML 資料，則可使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="2f856-390">If you are not replicating XML data, this parameter can be used.</span></span> <span data-ttu-id="2f856-391">這個參數無法搭配字元模式快照集使用。</span><span class="sxs-lookup"><span data-stu-id="2f856-391">This parameter cannot be used with character mode snapshots.</span></span> <span data-ttu-id="2f856-392">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果您使用這個參數，位於訂閱者端的  服務帳戶就必須擁有快照集 .bcp 資料檔案所在目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="2f856-392">If you use this parameter, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located.</span></span> <span data-ttu-id="2f856-393">沒有使用這個參數時，代理程式所載入的 ODBC 驅動程式就會從這些檔案中讀取，因此不會使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="2f856-393">When this parameter is not used, the ODBC driver loaded by the agent reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is not used.</span></span>  
  
 <span data-ttu-id="2f856-394">**-Validate** [**0**|**1**|**2**|**3**]</span><span class="sxs-lookup"><span data-stu-id="2f856-394">**-Validate** [**0**|**1**|**2**|**3**]</span></span>  
 <span data-ttu-id="2f856-395">指定是否應該在合併工作階段結束時完成驗證，而且如果是的話，應該完成哪一種驗證。</span><span class="sxs-lookup"><span data-stu-id="2f856-395">Specifies whether validation should be done at the end of the merge session, and, if so, what type of validation.</span></span> <span data-ttu-id="2f856-396">值 **3** 是建議值。</span><span class="sxs-lookup"><span data-stu-id="2f856-396">The value of **3** is the recommended value.</span></span>  
  
|<span data-ttu-id="2f856-397">Validate 值</span><span class="sxs-lookup"><span data-stu-id="2f856-397">Validate value</span></span>|<span data-ttu-id="2f856-398">描述</span><span class="sxs-lookup"><span data-stu-id="2f856-398">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2f856-399">**0** (預設)</span><span class="sxs-lookup"><span data-stu-id="2f856-399">**0** (default)</span></span>|<span data-ttu-id="2f856-400">不驗證。</span><span class="sxs-lookup"><span data-stu-id="2f856-400">No validation.</span></span>|  
|<span data-ttu-id="2f856-401">**1**</span><span class="sxs-lookup"><span data-stu-id="2f856-401">**1**</span></span>|<span data-ttu-id="2f856-402">僅驗證資料列計數。</span><span class="sxs-lookup"><span data-stu-id="2f856-402">Rowcount-only validation.</span></span>|  
|<span data-ttu-id="2f856-403">**2**</span><span class="sxs-lookup"><span data-stu-id="2f856-403">**2**</span></span>|<span data-ttu-id="2f856-404">資料列計數及總和檢查碼驗證。</span><span class="sxs-lookup"><span data-stu-id="2f856-404">Rowcount and checksum validation.</span></span>|  
|<span data-ttu-id="2f856-405">**3**</span><span class="sxs-lookup"><span data-stu-id="2f856-405">**3**</span></span>|<span data-ttu-id="2f856-406">資料列計數及二進位總和檢查碼驗證。</span><span class="sxs-lookup"><span data-stu-id="2f856-406">Rowcount and binary checksum validation.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="2f856-407">如果「訂閱者」與「發行者」端的資料類型不同，則使用二進位總和檢查碼或總和檢查碼的驗證可能會誤報失敗。</span><span class="sxs-lookup"><span data-stu-id="2f856-407">Validation by using binary checksum or checksum can incorrectly report a failure if data types are different at the Subscriber than they are at the Publisher.</span></span> <span data-ttu-id="2f856-408">如需詳細資訊，請參閱[驗證複寫的資料](../validate-data-at-the-subscriber.md)中的＜資料驗證的考量＞一節。</span><span class="sxs-lookup"><span data-stu-id="2f856-408">For more information, see the section "Considerations for Data Validation" in [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span>  
  
 <span data-ttu-id="2f856-409">**-ValidateInterval** _validate_interval_</span><span class="sxs-lookup"><span data-stu-id="2f856-409">**-ValidateInterval** _validate_interval_</span></span>  
 <span data-ttu-id="2f856-410">這是在連續模式下驗證訂閱的頻率。</span><span class="sxs-lookup"><span data-stu-id="2f856-410">Is how often, in minutes, the subscription is validated in continuous mode.</span></span> <span data-ttu-id="2f856-411">預設值是 **60** 分鐘。</span><span class="sxs-lookup"><span data-stu-id="2f856-411">The default is **60** minutes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f856-412">備註</span><span class="sxs-lookup"><span data-stu-id="2f856-412">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2f856-413">如果您已將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 安裝成在本機系統帳戶而非網域使用者帳戶 (預設值) 底下執行，這項服務就只能存取本機電腦。</span><span class="sxs-lookup"><span data-stu-id="2f856-413">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account rather than under a domain user account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="2f856-414">如果在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 底下執行的合併代理程式設定為使用 Windows 驗證模式，當它登入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]時，合併代理程式就會失敗。</span><span class="sxs-lookup"><span data-stu-id="2f856-414">If the Merge Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Merge Agent fails.</span></span> <span data-ttu-id="2f856-415">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設設定為  驗證。</span><span class="sxs-lookup"><span data-stu-id="2f856-415">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="2f856-416">若要啟動合併代理程式，請從命令提示字元執行 **replmerg.exe** 。</span><span class="sxs-lookup"><span data-stu-id="2f856-416">To start the Merge Agent, execute **replmerg.exe** from the command prompt.</span></span> <span data-ttu-id="2f856-417">如需詳細資訊，請參閱＜ [複寫代理程式可執行檔](../concepts/replication-agent-executables-concepts.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2f856-417">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
 <span data-ttu-id="2f856-418">在連續模式執行時，不會移除目前工作階段的合併代理程式記錄。</span><span class="sxs-lookup"><span data-stu-id="2f856-418">The merge agent history for the current session is not removed while running in continuous mode.</span></span> <span data-ttu-id="2f856-419">長時間執行的代理程式會在合併記錄資料表中產生可能會影響效能的大量項目。</span><span class="sxs-lookup"><span data-stu-id="2f856-419">A long running agent can result in a large number of entries in the merge history tables which could impact performance.</span></span> <span data-ttu-id="2f856-420">若要解決這個問題，請切換到排程模式或是繼續使用連續模式，但是要建立專門作業來定期重新啟動合併代理程式，或是減少記錄層級的詳細資訊來減少資料列數，這樣會降低效能影響。</span><span class="sxs-lookup"><span data-stu-id="2f856-420">To resolve this problem switch to scheduled mode, or continue to use continuous mode but create a dedicated job to periodically restart the merge agent, or reduce the verbosity of the history level to reduce the number of rows and therefor reduce the performance impact.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f856-421">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f856-421">See Also</span></span>  
 [<span data-ttu-id="2f856-422">複寫代理程式管理</span><span class="sxs-lookup"><span data-stu-id="2f856-422">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
