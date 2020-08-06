---
title: 複寫快照集代理程式 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a26aca7b33a7355500350572ea5e8ed21bddeacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585896"
---
# <a name="replication-snapshot-agent"></a><span data-ttu-id="50552-102">複寫快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="50552-102">Replication Snapshot Agent</span></span>
  <span data-ttu-id="50552-103">「複寫快照集代理程式」是一個可執行檔，它會準備包含已發行資料表與資料庫物件之結構描述及資料的快照集檔案、將這些檔案儲存在快照集資料夾內，然後記錄散發資料庫中的同步處理作業。</span><span class="sxs-lookup"><span data-stu-id="50552-103">The Replication Snapshot Agent is an executable file that prepares snapshot files containing schema and data of published tables and database objects, stores the files in the snapshot folder, and records synchronization jobs in the distribution database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50552-104">您可以使用任何順序來指定參數。</span><span class="sxs-lookup"><span data-stu-id="50552-104">Parameters can be specified in any order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50552-105">語法</span><span class="sxs-lookup"><span data-stu-id="50552-105">Syntax</span></span>  
  
```  
  
      snapshot [ -?]   
-Publisherserver_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSizebcp_batch_size]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostNamedynamic_filter_host_name]  
[-DynamicFilterLogindynamic_filter_login]  
[-DynamicSnapshotLocationdynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiterfield_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocksnumber_of_blocks ]  
[-HRBcpBlockSizeblock_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageIntervalkeep_alive_interval]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreadsnumber_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSizepacket_size]
[-PrefetchTables [0|1] ]  
[-ProfileNameprofile_name]  
[-PublisherDBpublisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOutquery_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiterrow_delimiter]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-UsePerArticleContentsViewuse_per_article_contents_view]  
```  
  
## <a name="arguments"></a><span data-ttu-id="50552-106">引數</span><span class="sxs-lookup"><span data-stu-id="50552-106">Arguments</span></span>  
 <span data-ttu-id="50552-107">**-?**</span><span class="sxs-lookup"><span data-stu-id="50552-107">**-?**</span></span>  
 <span data-ttu-id="50552-108">列印所有可用的參數。</span><span class="sxs-lookup"><span data-stu-id="50552-108">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="50552-109">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="50552-109">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="50552-110">這是發行者的名稱。</span><span class="sxs-lookup"><span data-stu-id="50552-110">Is the name of the Publisher.</span></span> <span data-ttu-id="50552-111">請針對該伺服器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="50552-111">Specify server_name for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="50552-112">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="50552-112">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="50552-113">**-Publication** _publication_</span><span class="sxs-lookup"><span data-stu-id="50552-113">**-Publication** _publication_</span></span>  
 <span data-ttu-id="50552-114">這是發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="50552-114">Is the name of the publication.</span></span> <span data-ttu-id="50552-115">只有在發行集設定成隨時都有快照供新的訂閱或重新初始化的訂閱使用時，這個參數才有效。</span><span class="sxs-lookup"><span data-stu-id="50552-115">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="50552-116">**-70Subscribers**</span><span class="sxs-lookup"><span data-stu-id="50552-116">**-70Subscribers**</span></span>  
 <span data-ttu-id="50552-117">如果有任何訂閱者正在執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 版，您就必須使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="50552-117">Must be used if any Subscribers are running [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version 7.0.</span></span>  
  
 <span data-ttu-id="50552-118">**-BcpBatchSize** _bcp_\_ *batch*\_ *size*</span><span class="sxs-lookup"><span data-stu-id="50552-118">**-BcpBatchSize** _bcp_\_ *batch*\_ *size*</span></span>  
 <span data-ttu-id="50552-119">這是要在大量複製作業中傳送的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="50552-119">Is the number of rows to send in a bulk copy operation.</span></span> <span data-ttu-id="50552-120">執行 **bcp in** 作業時，批次大小就是要在單一交易中傳送至伺服器的資料列數目，而且它也是「散發代理程式」記錄 **bcp** 進度訊息之前必須傳送的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="50552-120">When performing a **bcp in** operation, the batch size is the number of rows to send to the server as one transaction, and also the number of rows that must be sent before the Distribution Agent logs a **bcp** progress message.</span></span> <span data-ttu-id="50552-121">執行 **bcp out** 作業時，系統會使用固定批次大小 1000。</span><span class="sxs-lookup"><span data-stu-id="50552-121">When performing a **bcp out** operation, a fixed batch size of 1000 is used.</span></span> <span data-ttu-id="50552-122">值為 0 表示沒有記錄任何訊息。</span><span class="sxs-lookup"><span data-stu-id="50552-122">A value of 0 indicates no message logging.</span></span>  
  
 <span data-ttu-id="50552-123">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="50552-123">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="50552-124">這是代理程式定義檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="50552-124">Is the path of the agent definition file.</span></span> <span data-ttu-id="50552-125">代理程式定義檔包含代理程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="50552-125">An agent definition file contains command line arguments for the agent.</span></span> <span data-ttu-id="50552-126">此檔案的內容會剖析為可執行檔。</span><span class="sxs-lookup"><span data-stu-id="50552-126">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="50552-127">請使用雙引號 (") 來指定包含任意字元的引數值。</span><span class="sxs-lookup"><span data-stu-id="50552-127">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="50552-128">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="50552-128">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="50552-129">這是散發者的名稱。</span><span class="sxs-lookup"><span data-stu-id="50552-129">Is the Distributor name.</span></span> <span data-ttu-id="50552-130">請針對該伺服器上的 *預設執行個體指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="50552-130">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="50552-131">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="50552-131">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="50552-132">**-DistributorDeadlockPriority** [ **-1**|**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="50552-132">**-DistributorDeadlockPriority** [**-1**|**0**|**1**]</span></span>  
 <span data-ttu-id="50552-133">這是發生死結時散發者之快照集代理程式連接的優先權。</span><span class="sxs-lookup"><span data-stu-id="50552-133">Is the priority of the Snapshot Agent connection to the Distributor when a deadlock occurs.</span></span> <span data-ttu-id="50552-134">指定這個參數的目的是為了解決快照集產生期間，快照集代理程式與使用者應用程式之間可能會發生的死結。</span><span class="sxs-lookup"><span data-stu-id="50552-134">This parameter is specified to resolve deadlocks that may occur between the Snapshot Agent and user applications during snapshot generation.</span></span>  
  
|<span data-ttu-id="50552-135">DistributorDeadlockPriority 值</span><span class="sxs-lookup"><span data-stu-id="50552-135">DistributorDeadlockPriority value</span></span>|<span data-ttu-id="50552-136">描述</span><span class="sxs-lookup"><span data-stu-id="50552-136">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="50552-137">**-1**</span><span class="sxs-lookup"><span data-stu-id="50552-137">**-1**</span></span>|<span data-ttu-id="50552-138">在散發者端發生死結時，快照集代理程式以外的應用程式擁有優先權。</span><span class="sxs-lookup"><span data-stu-id="50552-138">Applications other than the Snapshot Agent have priority when a deadlock occurs at the Distributor.</span></span>|  
|<span data-ttu-id="50552-139">**0** (預設值)</span><span class="sxs-lookup"><span data-stu-id="50552-139">**0** (Default)</span></span>|<span data-ttu-id="50552-140">未指派優先權。</span><span class="sxs-lookup"><span data-stu-id="50552-140">Priority is not assigned.</span></span>|  
|<span data-ttu-id="50552-141">**1**</span><span class="sxs-lookup"><span data-stu-id="50552-141">**1**</span></span>|<span data-ttu-id="50552-142">在散發者端發生死結時，快照集代理程式擁有優先權。</span><span class="sxs-lookup"><span data-stu-id="50552-142">Snapshot Agent has priority when a deadlock occurs at the Distributor.</span></span>|  
  
 <span data-ttu-id="50552-143">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="50552-143">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="50552-144">這是連接至使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證的散發者時，系統所使用的登入。</span><span class="sxs-lookup"><span data-stu-id="50552-144">Is the login used when connecting to the Distributor using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="50552-145">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="50552-145">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="50552-146">這是連接至使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證的散發者時，系統所使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="50552-146">Is the password used when connecting to the Distributor using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="50552-147">.</span><span class="sxs-lookup"><span data-stu-id="50552-147">.</span></span>  
  
 <span data-ttu-id="50552-148">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="50552-148">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="50552-149">指定散發者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="50552-149">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="50552-150">值為 **0** 表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證模式 (預設值)，而值為 **1** 則表示 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="50552-150">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="50552-151">**-DynamicFilterHostName** _dynamic_filter_host_name_</span><span class="sxs-lookup"><span data-stu-id="50552-151">**-DynamicFilterHostName** _dynamic_filter_host_name_</span></span>  
 <span data-ttu-id="50552-152">這是建立動態快照集時，用來進行篩選所設定的 [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) 值。</span><span class="sxs-lookup"><span data-stu-id="50552-152">Is used to set a value for [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) in filtering when a dynamic snapshot is created.</span></span> <span data-ttu-id="50552-153">例如，如果已針對發行項指定了子集篩選子句 `rep_id = HOST_NAME()` ，而且您在呼叫「合併代理程式」之前將 **DynamicFilterHostName** 屬性設定為 "FBJones"，系統就只會複寫 **rep_id** 資料行中具有 "FBJones" 的資料列。</span><span class="sxs-lookup"><span data-stu-id="50552-153">For example, if the subset filter clause `rep_id = HOST_NAME()` is specified for an article, and you set the **DynamicFilterHostName** property to "FBJones" before calling the Merge Agent, only rows having "FBJones" in the **rep_id** column will be replicated.</span></span>  
  
 <span data-ttu-id="50552-154">**-DynamicFilterLogin** _dynamic_filter_login_</span><span class="sxs-lookup"><span data-stu-id="50552-154">**-DynamicFilterLogin** _dynamic_filter_login_</span></span>  
 <span data-ttu-id="50552-155">這是建立動態快照集時，用來進行篩選所設定的 [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) 值。</span><span class="sxs-lookup"><span data-stu-id="50552-155">Is used to set a value for [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql)in filtering when a dynamic snapshot is created.</span></span> <span data-ttu-id="50552-156">例如，如果已針對發行項指定了子集篩選子句 `user_id = SUSER_SNAME()` ，而且您在呼叫 **SQLSnapshot** 物件的 **Run** 方法之前將 **DynamicFilterLogin** 屬性設定為 "rsmith"，就只有 **user_id** 資料行中具有 "rsmith" 的資料列會加入快照集中。</span><span class="sxs-lookup"><span data-stu-id="50552-156">For example, if the subset filter clause `user_id = SUSER_SNAME()` is specified for an article, and you set the **DynamicFilterLogin** property to "rsmith" before calling the **Run** method of the **SQLSnapshot** object, only rows having "rsmith" in the **user_id** column will be included in the snapshot.</span></span>  
  
 <span data-ttu-id="50552-157">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span><span class="sxs-lookup"><span data-stu-id="50552-157">**-DynamicSnapshotLocation** _dynamic_snapshot_location_</span></span>  
 <span data-ttu-id="50552-158">這是應該產生動態快照集的位置。</span><span class="sxs-lookup"><span data-stu-id="50552-158">Is the location where the dynamic snapshot should be generated.</span></span>  
  
 <span data-ttu-id="50552-159">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="50552-159">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="50552-160">這是建立連接時，快照集代理程式所使用的安全通訊端層 (SSL) 加密層級。</span><span class="sxs-lookup"><span data-stu-id="50552-160">Is the level of Secure Sockets Layer (SSL) encryption used by the Snapshot Agent when making connections.</span></span>  
  
|<span data-ttu-id="50552-161">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="50552-161">EncryptionLevel value</span></span>|<span data-ttu-id="50552-162">描述</span><span class="sxs-lookup"><span data-stu-id="50552-162">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="50552-163">**0**</span><span class="sxs-lookup"><span data-stu-id="50552-163">**0**</span></span>|<span data-ttu-id="50552-164">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="50552-164">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="50552-165">**1**</span><span class="sxs-lookup"><span data-stu-id="50552-165">**1**</span></span>|<span data-ttu-id="50552-166">指定要使用 SSL，但是代理程式不會驗證 SSL 伺服器憑證是否由受信任的簽發者簽署。</span><span class="sxs-lookup"><span data-stu-id="50552-166">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="50552-167">**2**</span><span class="sxs-lookup"><span data-stu-id="50552-167">**2**</span></span>|<span data-ttu-id="50552-168">指定要使用 SSL，而且憑證會經過驗證。</span><span class="sxs-lookup"><span data-stu-id="50552-168">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="50552-169">定義的 SSL 憑證必須包含 SQL Server 的完整網域名稱才會有效。</span><span class="sxs-lookup"><span data-stu-id="50552-169">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="50552-170">為了讓代理程式能在將 -EncryptionLevel 設定為 2 時成功連線，請在本機 SQL Server 上建立別名。</span><span class="sxs-lookup"><span data-stu-id="50552-170">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="50552-171">'Alias Name' 參數應為伺服器名稱，且應將 'Server' 參數設為 SQL Server 的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="50552-171">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="50552-172">如需詳細資訊，請參閱[SQL Server 複寫安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="50552-172">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="50552-173">**-FieldDelimiter** _field_delimiter_</span><span class="sxs-lookup"><span data-stu-id="50552-173">**-FieldDelimiter** _field_delimiter_</span></span>  
 <span data-ttu-id="50552-174">這是在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大量複製資料檔案中標示欄位結尾的字元或字元序列。</span><span class="sxs-lookup"><span data-stu-id="50552-174">Is the character or character sequence that marks the end of a field in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bulk-copy data file.</span></span> <span data-ttu-id="50552-175">預設為 \n\<x$3>\n。</span><span class="sxs-lookup"><span data-stu-id="50552-175">The default is \n\<x$3>\n.</span></span>  
  
 <span data-ttu-id="50552-176">**-HistoryVerboseLevel** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="50552-176">**-HistoryVerboseLevel** [ **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="50552-177">指定在快照集作業期間記錄的記錄量。</span><span class="sxs-lookup"><span data-stu-id="50552-177">Specifies the amount of history logged during a snapshot operation.</span></span> <span data-ttu-id="50552-178">您可以透過選取 **1**，盡量減少記錄作業對效能造成的影響。</span><span class="sxs-lookup"><span data-stu-id="50552-178">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="50552-179">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="50552-179">HistoryVerboseLevel value</span></span>|<span data-ttu-id="50552-180">描述</span><span class="sxs-lookup"><span data-stu-id="50552-180">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="50552-181">**0**</span><span class="sxs-lookup"><span data-stu-id="50552-181">**0**</span></span>|<span data-ttu-id="50552-182">進度訊息會寫入主控台或輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="50552-182">Progress messages are written either to the console or to an output file.</span></span> <span data-ttu-id="50552-183">但是，記錄不會記錄在散發資料庫中。</span><span class="sxs-lookup"><span data-stu-id="50552-183">History records are not logged in the distribution database.</span></span>|  
|<span data-ttu-id="50552-184">**1**</span><span class="sxs-lookup"><span data-stu-id="50552-184">**1**</span></span>|<span data-ttu-id="50552-185">一律更新相同狀態的上一個記錄訊息 (啟動、進度、成功等等)。</span><span class="sxs-lookup"><span data-stu-id="50552-185">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="50552-186">如果沒有任何具有相同狀態的上一筆記錄存在，便插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="50552-186">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="50552-187">**2** (預設值)</span><span class="sxs-lookup"><span data-stu-id="50552-187">**2** (default)</span></span>|<span data-ttu-id="50552-188">除非記錄用於閒置訊息或長時間執行作業訊息等事件 (在此情況下，更新之前的記錄)，否則便插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="50552-188">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
|<span data-ttu-id="50552-189">**3**</span><span class="sxs-lookup"><span data-stu-id="50552-189">**3**</span></span>|<span data-ttu-id="50552-190">除非記錄用於閒置訊息，否則一律插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="50552-190">Always insert new records, unless it is for idle messages.</span></span>|  
  
 <span data-ttu-id="50552-191">**-HRBcpBlocks** _number_of_blocks_</span><span class="sxs-lookup"><span data-stu-id="50552-191">**-HRBcpBlocks** _number_of_blocks_</span></span>  
 <span data-ttu-id="50552-192">這是在寫入器與讀取器執行緒之間排入佇列的 **bcp** 資料區塊數目。</span><span class="sxs-lookup"><span data-stu-id="50552-192">Is the number of **bcp** data blocks that are queued between the writer and reader threads.</span></span> <span data-ttu-id="50552-193">預設值是 50。</span><span class="sxs-lookup"><span data-stu-id="50552-193">The default value is 50.</span></span> <span data-ttu-id="50552-194">**HRBcpBlocks** 只能搭配 Oracle 發行集使用。</span><span class="sxs-lookup"><span data-stu-id="50552-194">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50552-195">這個參數是用於從 Oracle 發行者進行 **bcp** 效能的效能微調。</span><span class="sxs-lookup"><span data-stu-id="50552-195">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="50552-196">-**HRBcpBlockSize**_block_size_</span><span class="sxs-lookup"><span data-stu-id="50552-196">-**HRBcpBlockSize**_block_size_</span></span>  
 <span data-ttu-id="50552-197">這是每個 **bcp** 資料區塊的大小 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="50552-197">Is the size, in kilobytes (KB), of each **bcp** data block.</span></span> <span data-ttu-id="50552-198">預設值為 64 KB。</span><span class="sxs-lookup"><span data-stu-id="50552-198">The default value is 64 KB.</span></span> <span data-ttu-id="50552-199">**HRBcpBlocks** 只能搭配 Oracle 發行集使用。</span><span class="sxs-lookup"><span data-stu-id="50552-199">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50552-200">這個參數是用於從 Oracle 發行者進行 **bcp** 效能的效能微調。</span><span class="sxs-lookup"><span data-stu-id="50552-200">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="50552-201">**-HRBcpDynamicBlocks**</span><span class="sxs-lookup"><span data-stu-id="50552-201">**-HRBcpDynamicBlocks**</span></span>  
 <span data-ttu-id="50552-202">這是指每個 **bcp** 資料區塊的大小是否可以動態地成長。</span><span class="sxs-lookup"><span data-stu-id="50552-202">Is whether or not the size of each **bcp** data block can grow dynamically.</span></span> <span data-ttu-id="50552-203">**HRBcpBlocks** 只能搭配 Oracle 發行集使用。</span><span class="sxs-lookup"><span data-stu-id="50552-203">**HRBcpBlocks** is only used with Oracle publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50552-204">這個參數是用於從 Oracle 發行者進行 **bcp** 效能的效能微調。</span><span class="sxs-lookup"><span data-stu-id="50552-204">This parameter is used for performance tuning of **bcp** performance from an Oracle Publisher.</span></span>  
  
 <span data-ttu-id="50552-205">**-KeepAliveMessageInterval** _keep_alive_interval_</span><span class="sxs-lookup"><span data-stu-id="50552-205">**-KeepAliveMessageInterval** _keep_alive_interval_</span></span>  
 <span data-ttu-id="50552-206">這是將「正在等候後端訊息」記錄至 [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) 資料表之前，快照集代理程式等候的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="50552-206">Is the amount of time, in seconds, that the Snapshot Agent waits before logging "waiting for backend message" to the [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) table.</span></span> <span data-ttu-id="50552-207">預設值為 300 秒。</span><span class="sxs-lookup"><span data-stu-id="50552-207">The default value is 300 seconds.</span></span>  
  
 <span data-ttu-id="50552-208">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="50552-208">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="50552-209">這是登入逾時之前的秒數。 預設值為 15 秒。</span><span class="sxs-lookup"><span data-stu-id="50552-209">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="50552-210">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="50552-210">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="50552-211">指定可用平行方式執行的大量複製作業數目。</span><span class="sxs-lookup"><span data-stu-id="50552-211">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="50552-212">同時存在之執行緒和 ODBC 連接的最大數目是 **MaxBcpThreads** 或散發資料庫之同步處理交易中顯示的大量複製要求數目的較小者。</span><span class="sxs-lookup"><span data-stu-id="50552-212">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the synchronization transaction in the distribution database.</span></span> <span data-ttu-id="50552-213">**MaxBcpThreads** 必須具有大於 **0** 的值而且沒有硬式編碼的上限。</span><span class="sxs-lookup"><span data-stu-id="50552-213">**MaxBcpThreads** must have a value greater than **0** and has no hard-coded upper limit.</span></span> <span data-ttu-id="50552-214">預設為 **1**。</span><span class="sxs-lookup"><span data-stu-id="50552-214">The default is **1**.</span></span>  
  
 <span data-ttu-id="50552-215">\- **MaxNetworkOptimization** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="50552-215">\- **MaxNetworkOptimization** [ **0**| **1**]</span></span>  
 <span data-ttu-id="50552-216">這是指無關的刪除動作是否會傳送至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="50552-216">Is if irrelevant deletes are sent to the Subscriber.</span></span> <span data-ttu-id="50552-217">無關的刪除動作是針對不屬於訂閱者資料分割的資料列傳送至訂閱者的 DELETE 命令。</span><span class="sxs-lookup"><span data-stu-id="50552-217">Irrelevant deletes are DELETE commands that are sent to Subscribers for rows that do not belong to the Subscriber's partition.</span></span> <span data-ttu-id="50552-218">雖然無關的刪除動作不會影響資料完整性或聚合，但是它們可能會產生不必要的網路流量。</span><span class="sxs-lookup"><span data-stu-id="50552-218">Irrelevant deletes do not affect data integrity or convergence, but they can result in unnecessary network traffic.</span></span> <span data-ttu-id="50552-219">**MaxNetworkOptimization** 的預設值為 **0**。</span><span class="sxs-lookup"><span data-stu-id="50552-219">The default value of **MaxNetworkOptimization** is **0**.</span></span> <span data-ttu-id="50552-220">將 **MaxNetworkOptimization** 設定為 **1** 會盡可能減少無關刪除動作的機會，因而縮減網路流量並擴大網路最佳化。</span><span class="sxs-lookup"><span data-stu-id="50552-220">Setting **MaxNetworkOptimization** to **1** minimizing the chances of irrelevant deletes thereby reducing network traffic and maximizing network optimization.</span></span> <span data-ttu-id="50552-221">如果聯結篩選和複雜子集篩選的多重層級存在，將這個參數設定為 **1** 也可能會增加中繼資料的儲存體，而且導致發行者端的效能降低。</span><span class="sxs-lookup"><span data-stu-id="50552-221">Setting this parameter to **1** can also increase the storage of metadata and cause performance to degrade at the Publisher if multiple levels of join filters and complex subset filters are present.</span></span> <span data-ttu-id="50552-222">您應該仔細地評估複寫拓撲，並且只有在無關刪除動作的網路流量高得無法接受，才將 **MaxNetworkOptimization** 設定為 **1** 。</span><span class="sxs-lookup"><span data-stu-id="50552-222">You should carefully assess your replication topology and set **MaxNetworkOptimization** to **1** only if network traffic from irrelevant deletes is unacceptably high.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50552-223">只有當合併式發行集的同步處理優化選項設定為**true**時，才會將此參數設定為**1** ， (**@keep_partition_changes** [sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)) 的參數。</span><span class="sxs-lookup"><span data-stu-id="50552-223">Setting this parameter to **1** is useful only when the synchronization optimization option of the merge publication is set to **true** (the **@keep_partition_changes** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).</span></span>  
  
 <span data-ttu-id="50552-224">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="50552-224">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="50552-225">這是代理程式輸出檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="50552-225">Is the path of the agent output file.</span></span> <span data-ttu-id="50552-226">如果未提供檔案名稱，輸出將傳送至主控台。</span><span class="sxs-lookup"><span data-stu-id="50552-226">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="50552-227">如果指定的檔案名稱存在，輸出就會附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="50552-227">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="50552-228">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="50552-228">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="50552-229">指定輸出是否應該詳細。</span><span class="sxs-lookup"><span data-stu-id="50552-229">Specifies whether the output should be verbose.</span></span>  
  
|<span data-ttu-id="50552-230">OutputVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="50552-230">OutputVerboseLevel value</span></span>|<span data-ttu-id="50552-231">描述</span><span class="sxs-lookup"><span data-stu-id="50552-231">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="50552-232">**0**</span><span class="sxs-lookup"><span data-stu-id="50552-232">**0**</span></span>|<span data-ttu-id="50552-233">僅列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="50552-233">Only error messages are printed.</span></span>|  
|<span data-ttu-id="50552-234">**1** (預設值)</span><span class="sxs-lookup"><span data-stu-id="50552-234">**1** (default)</span></span>|<span data-ttu-id="50552-235">列印所有進度報表訊息 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="50552-235">All the progress report messages are printed (default).</span></span>|  
|<span data-ttu-id="50552-236">**2**</span><span class="sxs-lookup"><span data-stu-id="50552-236">**2**</span></span>|<span data-ttu-id="50552-237">列印所有錯誤訊息和進度報表訊息 (可用於偵錯)。</span><span class="sxs-lookup"><span data-stu-id="50552-237">All error messages and progress report messages are printed, which is useful for debugging.</span></span>|  

 <span data-ttu-id="50552-238">**-PrefetchTables** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="50552-238">**-PrefetchTables** [ **0**| **1**]</span></span>  
 <span data-ttu-id="50552-239">指定是否要預先擷取並快取資料表物件的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="50552-239">Optional parameter that specifies if the table objects will be prefetched and cached.</span></span>  <span data-ttu-id="50552-240">預設行為是根據內部計算，使用 SMO 元件預先擷取特調資料表內容。</span><span class="sxs-lookup"><span data-stu-id="50552-240">The default behavior is to prefetch certain table properties using SMO component based on an internal calculation.</span></span>  <span data-ttu-id="50552-241">此參數在 SMO 預先擷取作業花非常長時間執行的情況下很實用。</span><span class="sxs-lookup"><span data-stu-id="50552-241">This parameter can be helpful in scenarios where SMO prefetch operation takes considerable longer to run.</span></span> <span data-ttu-id="50552-242">若未使用此參數，會在執行階段根據已新增為要發佈之發行項的資料表百分比來制訂決策。</span><span class="sxs-lookup"><span data-stu-id="50552-242">If this parameter is not used, this decision is made at runtime based on the percentage of tables that are added as articles to the publication.</span></span>  
  
|<span data-ttu-id="50552-243">OutputVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="50552-243">OutputVerboseLevel value</span></span>|<span data-ttu-id="50552-244">描述</span><span class="sxs-lookup"><span data-stu-id="50552-244">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="50552-245">**0**</span><span class="sxs-lookup"><span data-stu-id="50552-245">**0**</span></span>|<span data-ttu-id="50552-246">SMO 元件的「呼叫以預先擷取」方法已停用。</span><span class="sxs-lookup"><span data-stu-id="50552-246">Call to Prefetch method of SMO component is disabled.</span></span>|  
|<span data-ttu-id="50552-247">**1**</span><span class="sxs-lookup"><span data-stu-id="50552-247">**1**</span></span>|<span data-ttu-id="50552-248">「快照集代理程式」將會呼叫預先擷取方法以使用 SMO 快取某些資料表內容</span><span class="sxs-lookup"><span data-stu-id="50552-248">Snapshot Agent will call Prefetch method to cache some table properties using SMO</span></span>|  
  
 <span data-ttu-id="50552-249">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="50552-249">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="50552-250">這是快照集代理程式連接至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]時所使用的封包大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="50552-250">Is the packet size (in bytes) used by the Snapshot Agent when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="50552-251">預設值為 8192 個位元組。</span><span class="sxs-lookup"><span data-stu-id="50552-251">The default value is 8192 bytes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50552-252">除非確信有助於提升效能，否則請勿變更封包大小。</span><span class="sxs-lookup"><span data-stu-id="50552-252">Do not change the packet size unless you are certain that it will improve performance.</span></span> <span data-ttu-id="50552-253">對於大部分應用程式而言，預設封包大小是最適當的大小。</span><span class="sxs-lookup"><span data-stu-id="50552-253">For most applications, the default packet size is best.</span></span>  
  
 <span data-ttu-id="50552-254">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="50552-254">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="50552-255">指定要用於代理程式參數的代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="50552-255">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="50552-256">如果 **ProfileName** 為 NULL，就會停用代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="50552-256">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="50552-257">如果沒有指定 **ProfileName** ，就會使用該代理程式類型的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="50552-257">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="50552-258">如需資訊，請參閱[複寫代理程式設定檔](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="50552-258">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="50552-259">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="50552-259">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="50552-260">這是發行集資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="50552-260">Is the name of the publication database.</span></span> <span data-ttu-id="50552-261">*這個參數不支援 Oracle 發行者*。</span><span class="sxs-lookup"><span data-stu-id="50552-261">*This parameter is not supported for Oracle Publishers*.</span></span>  
  
 <span data-ttu-id="50552-262">**-PublisherDeadlockPriority** [ **-1**|**0**|**1**]</span><span class="sxs-lookup"><span data-stu-id="50552-262">**-PublisherDeadlockPriority** [**-1**|**0**|**1**]</span></span>  
 <span data-ttu-id="50552-263">這是發生死結時發行者之快照集代理程式連接的優先權。</span><span class="sxs-lookup"><span data-stu-id="50552-263">Is the priority of the Snapshot Agent connection to the Publisher when a deadlock occurs.</span></span> <span data-ttu-id="50552-264">指定這個參數的目的是為了解決快照集產生期間，快照集代理程式與使用者應用程式之間可能會發生的死結。</span><span class="sxs-lookup"><span data-stu-id="50552-264">This parameter is specified to resolve deadlocks that may occur between the Snapshot Agent and user applications during snapshot generation.</span></span>  
  
|<span data-ttu-id="50552-265">PublisherDeadlockPriority 值</span><span class="sxs-lookup"><span data-stu-id="50552-265">PublisherDeadlockPriority value</span></span>|<span data-ttu-id="50552-266">描述</span><span class="sxs-lookup"><span data-stu-id="50552-266">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="50552-267">**-1**</span><span class="sxs-lookup"><span data-stu-id="50552-267">**-1**</span></span>|<span data-ttu-id="50552-268">在發行者端發生死結時，快照集代理程式以外的應用程式擁有優先權。</span><span class="sxs-lookup"><span data-stu-id="50552-268">Applications other than the Snapshot Agent have priority when a deadlock occurs at the Publisher.</span></span>|  
|<span data-ttu-id="50552-269">**0** (預設值)</span><span class="sxs-lookup"><span data-stu-id="50552-269">**0** (Default)</span></span>|<span data-ttu-id="50552-270">未指派優先權。</span><span class="sxs-lookup"><span data-stu-id="50552-270">Priority is not assigned.</span></span>|  
|<span data-ttu-id="50552-271">**1**</span><span class="sxs-lookup"><span data-stu-id="50552-271">**1**</span></span>|<span data-ttu-id="50552-272">在發行者端發生死結時，快照集代理程式擁有優先權。</span><span class="sxs-lookup"><span data-stu-id="50552-272">Snapshot Agent has priority when a deadlock occurs at the Publisher.</span></span>|  
  
 <span data-ttu-id="50552-273">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="50552-273">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="50552-274">指定參與具有發行集資料庫之資料庫鏡像工作階段的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉夥伴執行個體。</span><span class="sxs-lookup"><span data-stu-id="50552-274">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="50552-275">如需詳細資訊，請參閱 [資料庫鏡像和複寫 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="50552-275">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="50552-276">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="50552-276">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="50552-277">這是連接至使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證的發行者時，系統所使用的登入。</span><span class="sxs-lookup"><span data-stu-id="50552-277">Is the login used when connecting to the Publisher using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="50552-278">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="50552-278">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="50552-279">這是連接至使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證的發行者時，系統所使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="50552-279">Is the password used when connecting to the Publisher using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="50552-280">.</span><span class="sxs-lookup"><span data-stu-id="50552-280">.</span></span>  
  
 <span data-ttu-id="50552-281">**-PublisherSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="50552-281">**-PublisherSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="50552-282">指定發行者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="50552-282">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="50552-283">值為 **0** 表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證 (預設值)，而值為 **1** 則表示 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="50552-283">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="50552-284">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="50552-284">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="50552-285">這是查詢逾時之前的秒數。預設值是 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="50552-285">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="50552-286">**-ReplicationType** [ **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="50552-286">**-ReplicationType** [ **1**| **2**]</span></span>  
 <span data-ttu-id="50552-287">指定複寫的類型。</span><span class="sxs-lookup"><span data-stu-id="50552-287">Specifies the type of replication.</span></span> <span data-ttu-id="50552-288">值為 **1** 表示異動複寫，而值為 **2** 則表示合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="50552-288">A value of **1** indicates transactional replication, and a value of **2** indicates merge replication.</span></span>  
  
 <span data-ttu-id="50552-289">**-RowDelimiter** _row_delimiter_</span><span class="sxs-lookup"><span data-stu-id="50552-289">**-RowDelimiter** _row_delimiter_</span></span>  
 <span data-ttu-id="50552-290">這是在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 大量複製資料檔案中標示資料列結尾的字元或字元序列。</span><span class="sxs-lookup"><span data-stu-id="50552-290">Is the character or character sequence that marks the end of a row in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bulk-copy data file.</span></span> <span data-ttu-id="50552-291">預設為 \n\<,@g>\n。</span><span class="sxs-lookup"><span data-stu-id="50552-291">The default is \n\<,@g>\n.</span></span>  
  
 <span data-ttu-id="50552-292">**-StartQueueTimeout** _start_queue_timeout_seconds_</span><span class="sxs-lookup"><span data-stu-id="50552-292">**-StartQueueTimeout** _start_queue_timeout_seconds_</span></span>  
 <span data-ttu-id="50552-293">這是當執行中並行動態快照集進程數目是由 **@max_concurrent_dynamic_snapshots** [Sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)的屬性所設定的限制時，快照集代理程式等待的最大秒數。</span><span class="sxs-lookup"><span data-stu-id="50552-293">Is the maximum number of seconds that the Snapshot Agent waits when the number of concurrent dynamic snapshot processes running is at the limit set by the **@max_concurrent_dynamic_snapshots** property of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="50552-294">如果已到達最大秒數而且快照集代理程式仍然等候中，它就會結束。</span><span class="sxs-lookup"><span data-stu-id="50552-294">If the maximum number of seconds is reached and the Snapshot Agent is still waiting, it will exit.</span></span> <span data-ttu-id="50552-295">值為 0 表示代理程式會永遠等候，不過您可以取消它。</span><span class="sxs-lookup"><span data-stu-id="50552-295">A value of 0 means that the agent waits indefinitely, although it can be canceled.</span></span>  
  
 <span data-ttu-id="50552-296">\- **UsePerArticleContentsView** _use_per_article_contents_view_</span><span class="sxs-lookup"><span data-stu-id="50552-296">\- **UsePerArticleContentsView** _use_per_article_contents_view_</span></span>  
 <span data-ttu-id="50552-297">這個參數已被取代，而且是為了回溯相容性才提供支援。</span><span class="sxs-lookup"><span data-stu-id="50552-297">This parameter has been deprecated and is supported for backward-compatibility only.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50552-298">備註</span><span class="sxs-lookup"><span data-stu-id="50552-298">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50552-299">如果您已將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 安裝成在本機系統帳戶而非網域使用者帳戶 (預設值) 底下執行，這項服務就只能存取本機電腦。</span><span class="sxs-lookup"><span data-stu-id="50552-299">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a Local System account rather than under a Domain User account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="50552-300">如果在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 底下執行的快照集代理程式設定為使用 Windows 驗證模式，當它登入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]時，快照集代理程式就會失敗。</span><span class="sxs-lookup"><span data-stu-id="50552-300">If the Snapshot Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Snapshot Agent fails.</span></span> <span data-ttu-id="50552-301">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設設定為  驗證。</span><span class="sxs-lookup"><span data-stu-id="50552-301">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="50552-302">若要啟動快照集代理程式，請從命令提示字元執行 **snapshot.exe** 。</span><span class="sxs-lookup"><span data-stu-id="50552-302">To start the Snapshot Agent, execute **snapshot.exe** from the command prompt.</span></span> <span data-ttu-id="50552-303">如需詳細資訊，請參閱＜ [複寫代理程式可執行檔](../concepts/replication-agent-executables-concepts.md)＞。</span><span class="sxs-lookup"><span data-stu-id="50552-303">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50552-304">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50552-304">See Also</span></span>  
 [<span data-ttu-id="50552-305">複寫代理程式管理</span><span class="sxs-lookup"><span data-stu-id="50552-305">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
