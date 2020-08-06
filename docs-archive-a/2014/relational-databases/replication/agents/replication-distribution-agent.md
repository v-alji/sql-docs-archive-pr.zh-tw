---
title: 複寫散發代理程式 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distribution Agent, executables
- agents [SQL Server replication], Distribution Agent
- Distribution Agent, parameter reference
- command prompt [SQL Server replication]
ms.assetid: 7b4fd480-9eaf-40dd-9a07-77301e44e2ac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5bd0b61626f4af268f93043114d5945d00a37b5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595924"
---
# <a name="replication-distribution-agent"></a><span data-ttu-id="796e3-102">複寫散發代理程式</span><span class="sxs-lookup"><span data-stu-id="796e3-102">Replication Distribution Agent</span></span>
  <span data-ttu-id="796e3-103">「複寫散發代理程式」是一個可執行檔，它會將快照集 (快照式複寫與異動複寫) 和散發資料庫資料表中保存的交易 (異動複寫) 移動至位於「訂閱者」端的目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="796e3-103">The Replication Distribution Agent is an executable that moves the snapshot (for snapshot replication and transactional replication) and the transactions held in the distribution database tables (for transactional replication) to the destination tables at the Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="796e3-104">您可以使用任何順序來指定參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-104">Parameters can be specified in any order.</span></span> <span data-ttu-id="796e3-105">沒有指定選擇性參數時，系統就會使用本機電腦上預先定義登錄設定的值。</span><span class="sxs-lookup"><span data-stu-id="796e3-105">When optional parameters are not specified, values from predefined registry settings on the local computer are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796e3-106">語法</span><span class="sxs-lookup"><span data-stu-id="796e3-106">Syntax</span></span>  
  
```  
  
      distrib [-?]  
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database   
[-AltSnapshotFolderalt_snapshot_folder_path]   
[-BcpBatchSizebcp_batch_size]  
[-CommitBatchSizecommit_batch_size]  
[-CommitBatchThresholdcommit_batch_threshold]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributordistributor]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ErrorFileerror_path_and_file_name]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-FileTransferType [0|1]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]   
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreads]  
[-MaxDeliveredTransactionsnumber_of_transactions]  
[-MessageIntervalmessage_interval]  
[-OledbStreamThresholdoledb_stream_threshold]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-Publicationpublication]  
[-QueryTimeOutquery_time_out_seconds]  
[-QuotedIdentifierquoted_identifier]  
[-SkipErrorsnative_error_id [:...n]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password]  
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|3]]  
[-SubscriptionStreams [1|2|...64]]  
[-SubscriptionTableNamesubscription_table]  
[-SubscriptionType [0|1|2]]  
[-TransactionsPerHistory [0|1|...10000]]  
[-UseDTS]  
[-UseInprocLoader]  
[-UseOledbStreaming]  
```  
  
## <a name="arguments"></a><span data-ttu-id="796e3-107">引數</span><span class="sxs-lookup"><span data-stu-id="796e3-107">Arguments</span></span>  
 <span data-ttu-id="796e3-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="796e3-108">**-?**</span></span>  
 <span data-ttu-id="796e3-109">列印所有可用的參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-109">Prints all available parameters.</span></span>  
  
 <span data-ttu-id="796e3-110">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="796e3-110">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="796e3-111">這是發行者的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-111">Is the name of the Publisher.</span></span> <span data-ttu-id="796e3-112">請針對該伺服器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 *server_name*。</span><span class="sxs-lookup"><span data-stu-id="796e3-112">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="796e3-113">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="796e3-113">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="796e3-114">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="796e3-114">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="796e3-115">這是發行者資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-115">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="796e3-116">**-Subscriber** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="796e3-116">**-Subscriber** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="796e3-117">這是訂閱者的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-117">Is the name of the Subscriber.</span></span> <span data-ttu-id="796e3-118">請針對該伺服器上的 *預設執行個體指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="796e3-118">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="796e3-119">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="796e3-119">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="796e3-120">**-SubscriberDB** _subscriber_database_</span><span class="sxs-lookup"><span data-stu-id="796e3-120">**-SubscriberDB** _subscriber_database_</span></span>  
 <span data-ttu-id="796e3-121">這是訂閱者資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-121">Is the name of the Subscriber database.</span></span>  
  
 <span data-ttu-id="796e3-122">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span><span class="sxs-lookup"><span data-stu-id="796e3-122">**-AltSnapshotFolder** _alt_snapshot_folder_path_</span></span>  
 <span data-ttu-id="796e3-123">這是包含訂閱之初始快照集的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="796e3-123">Is the path to the folder that contains the initial snapshot for a subscription.</span></span>  
  
 <span data-ttu-id="796e3-124">**-BcpBatchSize** _bcp_batch_size_</span><span class="sxs-lookup"><span data-stu-id="796e3-124">**-BcpBatchSize** _bcp_batch_size_</span></span>  
 <span data-ttu-id="796e3-125">這是要在大量複製作業中傳送的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="796e3-125">Is the number of rows to send in a bulk copy operation.</span></span> <span data-ttu-id="796e3-126">執行 **bcp in** 作業時，批次大小就是要在單一交易中傳送至伺服器的資料列數目，而且它也是「散發代理程式」記錄 **bcp** 進度訊息之前必須傳送的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="796e3-126">When performing a **bcp in** operation, the batch size is the number of rows to send to the server as one transaction, and also the number of rows that must be sent before the Distribution Agent logs a **bcp** progress message.</span></span> <span data-ttu-id="796e3-127">執行 **bcp out** 作業時，系統會使用固定批次大小 **1000** 。</span><span class="sxs-lookup"><span data-stu-id="796e3-127">When performing a **bcp out** operation, a fixed batch size of **1000** is used.</span></span>  
  
 <span data-ttu-id="796e3-128">**-CommitBatchSize** _commit_batch_size_</span><span class="sxs-lookup"><span data-stu-id="796e3-128">**-CommitBatchSize** _commit_batch_size_</span></span>  
 <span data-ttu-id="796e3-129">這是發出 COMMIT 陳述式之前，要發送至訂閱者的交易數目。</span><span class="sxs-lookup"><span data-stu-id="796e3-129">Is the number of transactions to be issued to the Subscriber before a COMMIT statement is issued.</span></span> <span data-ttu-id="796e3-130">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="796e3-130">The default is 100.</span></span>  
  
 <span data-ttu-id="796e3-131">**-CommitBatchThreshold**  _commit_batch_threshold_</span><span class="sxs-lookup"><span data-stu-id="796e3-131">**-CommitBatchThreshold**  _commit_batch_threshold_</span></span>  
 <span data-ttu-id="796e3-132">這是發出 COMMIT 陳述式之前，要發送至訂閱者的複寫命令數目。</span><span class="sxs-lookup"><span data-stu-id="796e3-132">Is the number of replication commands to be issued to the Subscriber before a COMMIT statement is issued.</span></span> <span data-ttu-id="796e3-133">預設值是 1000。</span><span class="sxs-lookup"><span data-stu-id="796e3-133">The default is 1000.</span></span>  
  
 <span data-ttu-id="796e3-134">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="796e3-134">**-Continuous**</span></span>  
 <span data-ttu-id="796e3-135">指定代理程式是否會嘗試持續輪詢複寫的交易。</span><span class="sxs-lookup"><span data-stu-id="796e3-135">Specifies whether the agent attempts to poll replicated transactions continually.</span></span> <span data-ttu-id="796e3-136">如果您指定了這個參數，代理程式就會以輪詢間隔輪詢來源的複寫交易，即使沒有任何交易暫止也一樣。</span><span class="sxs-lookup"><span data-stu-id="796e3-136">If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="796e3-137">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="796e3-137">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="796e3-138">這是代理程式定義檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="796e3-138">Is the path of the agent definition file.</span></span> <span data-ttu-id="796e3-139">代理程式定義檔包含代理程式的命令提示字元引數。</span><span class="sxs-lookup"><span data-stu-id="796e3-139">An agent definition file contains command prompt arguments for the agent.</span></span> <span data-ttu-id="796e3-140">此檔案的內容會剖析為可執行檔。</span><span class="sxs-lookup"><span data-stu-id="796e3-140">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="796e3-141">請使用雙引號 (") 來指定包含任意字元的引數值。</span><span class="sxs-lookup"><span data-stu-id="796e3-141">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="796e3-142">**-Distributor** _distributor_</span><span class="sxs-lookup"><span data-stu-id="796e3-142">**-Distributor** _distributor_</span></span>  
 <span data-ttu-id="796e3-143">這是散發者的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-143">Is the Distributor name.</span></span> <span data-ttu-id="796e3-144">若為散發者 (發送) 散發，此名稱會預設為本機散發者的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-144">For Distributor (push) distribution, the name defaults to the name of the local Distributor.</span></span>  
  
 <span data-ttu-id="796e3-145">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="796e3-145">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="796e3-146">這是散發者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-146">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="796e3-147">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="796e3-147">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="796e3-148">這是散發者密碼。</span><span class="sxs-lookup"><span data-stu-id="796e3-148">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="796e3-149">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="796e3-149">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="796e3-150">指定散發者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="796e3-150">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="796e3-151">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 值為 0 表示  驗證模式，而值為 1 則表示 Windows 驗證模式 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="796e3-151">A value of 0 indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode, and a value of 1 indicates Windows Authentication Mode (default).</span></span>  
  
 <span data-ttu-id="796e3-152">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="796e3-152">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="796e3-153">這是建立連接時，散發代理程式所使用的安全通訊端層 (SSL) 加密層級。</span><span class="sxs-lookup"><span data-stu-id="796e3-153">Is the level of Secure Sockets Layer (SSL) encryption used by the Distribution Agent when making connections.</span></span>  
  
|<span data-ttu-id="796e3-154">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="796e3-154">EncryptionLevel value</span></span>|<span data-ttu-id="796e3-155">描述</span><span class="sxs-lookup"><span data-stu-id="796e3-155">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="796e3-156">**0**</span><span class="sxs-lookup"><span data-stu-id="796e3-156">**0**</span></span>|<span data-ttu-id="796e3-157">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="796e3-157">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="796e3-158">**1**</span><span class="sxs-lookup"><span data-stu-id="796e3-158">**1**</span></span>|<span data-ttu-id="796e3-159">指定要使用 SSL，但是代理程式不會驗證 SSL 伺服器憑證是否由受信任的簽發者簽署。</span><span class="sxs-lookup"><span data-stu-id="796e3-159">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="796e3-160">**2**</span><span class="sxs-lookup"><span data-stu-id="796e3-160">**2**</span></span>|<span data-ttu-id="796e3-161">指定要使用 SSL，而且憑證會經過驗證。</span><span class="sxs-lookup"><span data-stu-id="796e3-161">Specifies that SSL is used, and that the certificate is verified.</span></span>|  
 
 > [!NOTE]  
 >  <span data-ttu-id="796e3-162">定義的 SSL 憑證必須包含 SQL Server 的完整網域名稱才會有效。</span><span class="sxs-lookup"><span data-stu-id="796e3-162">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="796e3-163">為了讓代理程式能在將 -EncryptionLevel 設定為 2 時成功連線，請在本機 SQL Server 上建立別名。</span><span class="sxs-lookup"><span data-stu-id="796e3-163">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="796e3-164">'Alias Name' 參數應為伺服器名稱，且應將 'Server' 參數設為 SQL Server 的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-164">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>

 <span data-ttu-id="796e3-165">如需詳細資訊，請參閱[SQL Server 複寫安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="796e3-165">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="796e3-166">**-ErrorFile** _error_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="796e3-166">**-ErrorFile** _error_path_and_file_name_</span></span>  
 <span data-ttu-id="796e3-167">這是由散發代理程式產生之錯誤檔的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-167">Is the path and file name of the error file generated by the Distribution Agent.</span></span> <span data-ttu-id="796e3-168">此檔案是在「訂閱者」端套用複寫交易時於發生故障處產生的；「發行者」或「散發者」端發生的錯誤將不記錄在此檔案中。</span><span class="sxs-lookup"><span data-stu-id="796e3-168">This file is generated at any point where failure occurred while applying replication transactions at the Subscriber; errors that occur at the Publisher or Distributor are not logged in this file.</span></span> <span data-ttu-id="796e3-169">此檔案包含失敗的複寫交易和相關的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="796e3-169">This file contains the failed replication transactions and associated error messages.</span></span> <span data-ttu-id="796e3-170">如果未指定，錯誤檔將在散發代理程式的目前目錄中產生。</span><span class="sxs-lookup"><span data-stu-id="796e3-170">When not specified, the error file is generated in the current directory of the Distribution Agent.</span></span> <span data-ttu-id="796e3-171">錯誤檔的名稱是含有 .err 副檔名的散發代理程式名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-171">The error file name is the name of the Distribution Agent with an .err extension.</span></span> <span data-ttu-id="796e3-172">如果指定的檔案名稱存在，錯誤訊息就會附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="796e3-172">If the specified file name exists, error messages are appended to the file.</span></span> <span data-ttu-id="796e3-173">這個參數最多可以有 256 個 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="796e3-173">This parameter can be a maximum of 256 Unicode characters.</span></span>  
  
 <span data-ttu-id="796e3-174">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="796e3-174">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span></span>  
 <span data-ttu-id="796e3-175">指定擴充的事件 XML 組態檔的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-175">Specifies the path and file name for the extended events XML configuration file.</span></span> <span data-ttu-id="796e3-176">擴充的事件組態檔可讓您設定工作階段以及啟用事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="796e3-176">The extended events configuration file allows you to configure sessions and enable events for tracking.</span></span>  
  
 <span data-ttu-id="796e3-177">**-FileTransferType** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="796e3-177">**-FileTransferType** [ **0**| **1**]</span></span>  
 <span data-ttu-id="796e3-178">指定檔案傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="796e3-178">Specifies the file transfer type.</span></span> <span data-ttu-id="796e3-179">值為 **0** 表示 UNC (通用命名慣例)，而值為 1 則表示 FTP (檔案傳輸通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="796e3-179">A value of **0** indicates UNC (universal naming convention), and a value of **1** indicates FTP (file transfer protocol).</span></span>  
  
 <span data-ttu-id="796e3-180">**-FtpAddress** _ftp_address_</span><span class="sxs-lookup"><span data-stu-id="796e3-180">**-FtpAddress** _ftp_address_</span></span>  
 <span data-ttu-id="796e3-181">這是散發者之 FTP 服務的網路位址。</span><span class="sxs-lookup"><span data-stu-id="796e3-181">Is the network address of the FTP service for the Distributor.</span></span> <span data-ttu-id="796e3-182">沒有指定這個參數時，系統就會使用 DistributorAddress。</span><span class="sxs-lookup"><span data-stu-id="796e3-182">When not specified, **DistributorAddress** is used.</span></span> <span data-ttu-id="796e3-183">如果沒有指定 **DistributorAddress** ，則會使用 Distributor。</span><span class="sxs-lookup"><span data-stu-id="796e3-183">If **DistributorAddress** is not specified, **Distributor** is used.</span></span>  
  
 <span data-ttu-id="796e3-184">**-FtpPassword** _ftp_password_</span><span class="sxs-lookup"><span data-stu-id="796e3-184">**-FtpPassword** _ftp_password_</span></span>  
 <span data-ttu-id="796e3-185">這是用來連接到 FTP 服務的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="796e3-185">Is the user password used to connect to the FTP service.</span></span>  
  
 <span data-ttu-id="796e3-186">**-FtpPort** _ftp_port_</span><span class="sxs-lookup"><span data-stu-id="796e3-186">**-FtpPort** _ftp_port_</span></span>  
 <span data-ttu-id="796e3-187">這是散發者的 FTP 服務通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="796e3-187">Is the port number of the FTP service for the Distributor.</span></span> <span data-ttu-id="796e3-188">沒有指定這個參數時，系統就會使用 FTP 服務的預設通訊埠編號 (21)。</span><span class="sxs-lookup"><span data-stu-id="796e3-188">When not specified, the default port number for FTP service (21) is used.</span></span>  
  
 <span data-ttu-id="796e3-189">**-FtpUserName**  _ftp_user_name_</span><span class="sxs-lookup"><span data-stu-id="796e3-189">**-FtpUserName**  _ftp_user_name_</span></span>  
 <span data-ttu-id="796e3-190">這是用來連接到 FTP 服務的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-190">Is the user name used to connect to the FTP service.</span></span> <span data-ttu-id="796e3-191"> 沒有指定這個參數時，系統就會使用 anonymous。</span><span class="sxs-lookup"><span data-stu-id="796e3-191">When not specified, **anonymous** is used.</span></span>  
  
 <span data-ttu-id="796e3-192">**-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]</span><span class="sxs-lookup"><span data-stu-id="796e3-192">**-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]</span></span>  
 <span data-ttu-id="796e3-193">指定在散發作業期間記錄的記錄量。</span><span class="sxs-lookup"><span data-stu-id="796e3-193">Specifies the amount of history logged during a distribution operation.</span></span> <span data-ttu-id="796e3-194">您可以透過選取 1，盡量減少記錄作業的效能影響。</span><span class="sxs-lookup"><span data-stu-id="796e3-194">You can minimize the performance effect of history logging by selecting **1**.</span></span>  
  
|<span data-ttu-id="796e3-195">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="796e3-195">HistoryVerboseLevel value</span></span>|<span data-ttu-id="796e3-196">描述</span><span class="sxs-lookup"><span data-stu-id="796e3-196">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="796e3-197">**0**</span><span class="sxs-lookup"><span data-stu-id="796e3-197">**0**</span></span>|<span data-ttu-id="796e3-198">進度訊息會寫入主控台或輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="796e3-198">Progress messages are written either to the console or to an output file.</span></span> <span data-ttu-id="796e3-199">但是，記錄不會記錄在散發資料庫中。</span><span class="sxs-lookup"><span data-stu-id="796e3-199">History records are not logged in the distribution database.</span></span>|  
|<span data-ttu-id="796e3-200">**1**</span><span class="sxs-lookup"><span data-stu-id="796e3-200">**1**</span></span>|<span data-ttu-id="796e3-201">預設值。</span><span class="sxs-lookup"><span data-stu-id="796e3-201">Default.</span></span> <span data-ttu-id="796e3-202">一律更新相同狀態的上一個記錄訊息 (啟動、進度、成功等等)。</span><span class="sxs-lookup"><span data-stu-id="796e3-202">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="796e3-203">如果沒有任何具有相同狀態的上一筆記錄存在，便插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="796e3-203">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="796e3-204">**2**</span><span class="sxs-lookup"><span data-stu-id="796e3-204">**2**</span></span>|<span data-ttu-id="796e3-205">除非記錄用於閒置訊息或長時間執行作業訊息等事件 (在此情況下，更新之前的記錄)，否則便插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="796e3-205">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
|<span data-ttu-id="796e3-206">**3**</span><span class="sxs-lookup"><span data-stu-id="796e3-206">**3**</span></span>|<span data-ttu-id="796e3-207">除非記錄用於閒置訊息，否則一律插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="796e3-207">Always insert new records, unless it is for idle messages.</span></span>|  
  
 <span data-ttu-id="796e3-208">**-Hostname** _host_name_</span><span class="sxs-lookup"><span data-stu-id="796e3-208">**-Hostname** _host_name_</span></span>  
 <span data-ttu-id="796e3-209">這是連接到發行者時所用的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-209">Is the host name used when connecting to the Publisher.</span></span> <span data-ttu-id="796e3-210">這個參數最多可以有 128 個 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="796e3-210">This parameter can be a maximum of 128 Unicode characters.</span></span>  
  
 <span data-ttu-id="796e3-211">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="796e3-211">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="796e3-212">這是記錄執行緒檢查是否有任何現有的連接正在等候伺服器回應之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="796e3-212">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="796e3-213">執行長時間執行的批次時，您可以減少這個值，避免檢查代理程式將散發代理程式標示為有疑問。</span><span class="sxs-lookup"><span data-stu-id="796e3-213">This value can be decreased to avoid having the checkup agent mark the Distribution Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="796e3-214">預設值是 **300** 秒。</span><span class="sxs-lookup"><span data-stu-id="796e3-214">The default is **300** seconds.</span></span>  
  
 <span data-ttu-id="796e3-215">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="796e3-215">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="796e3-216">這是登入逾時之前的秒數。 預設值為 15 秒。</span><span class="sxs-lookup"><span data-stu-id="796e3-216">Is the number of seconds before the login times out. The default is **15** seconds.</span></span>  
  
 <span data-ttu-id="796e3-217">**-MaxBcpThreads** _number_of_threads_</span><span class="sxs-lookup"><span data-stu-id="796e3-217">**-MaxBcpThreads** _number_of_threads_</span></span>  
 <span data-ttu-id="796e3-218">指定可用平行方式執行的大量複製作業數目。</span><span class="sxs-lookup"><span data-stu-id="796e3-218">Specifies the number of bulk copy operations that can be performed in parallel.</span></span> <span data-ttu-id="796e3-219">同時存在之執行緒和 ODBC 連接的最大數目是 **MaxBcpThreads** 或散發資料庫之同步處理交易中顯示的大量複製要求數目的較小者。</span><span class="sxs-lookup"><span data-stu-id="796e3-219">The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the synchronization transaction in the distribution database.</span></span> <span data-ttu-id="796e3-220">**MaxBcpThreads** 必須具有大於 **0** 的值而且沒有硬式編碼的上限。</span><span class="sxs-lookup"><span data-stu-id="796e3-220">**MaxBcpThreads** must have a value greater than **0** and has no hard-coded upper limit.</span></span> <span data-ttu-id="796e3-221">預設值為 **2**乘以處理器的數目，最大值是 8。</span><span class="sxs-lookup"><span data-stu-id="796e3-221">The default is **2** times the number of processors, up to a maximum value of **8**.</span></span> <span data-ttu-id="796e3-222">當使用並行快照集選項來套用在發行者端產生的快照集時，系統會使用單一執行緒，不論您針對 **MaxBcpThreads**指定的數目為何都一樣。</span><span class="sxs-lookup"><span data-stu-id="796e3-222">When applying a snapshot that was generated at the Publisher using the concurrent snapshot option, one thread is used, regardless of the number you specify for **MaxBcpThreads**.</span></span>  
  
 <span data-ttu-id="796e3-223">**-MaxDeliveredTransactions** _number_of_transactions_</span><span class="sxs-lookup"><span data-stu-id="796e3-223">**-MaxDeliveredTransactions** _number_of_transactions_</span></span>  
 <span data-ttu-id="796e3-224">這是在單一同步處理作業中套用至訂閱者的最大發送或提取交易數目。</span><span class="sxs-lookup"><span data-stu-id="796e3-224">Is the maximum number of push or pull transactions applied to Subscribers in one synchronization.</span></span> <span data-ttu-id="796e3-225">值為 0 表示最大值是無限個交易。</span><span class="sxs-lookup"><span data-stu-id="796e3-225">A value of **0** indicates that the maximum is an infinite number of transactions.</span></span> <span data-ttu-id="796e3-226">訂閱者可以使用其他值來縮短從發行者提取之同步處理作業的持續時間。</span><span class="sxs-lookup"><span data-stu-id="796e3-226">Other values can be used by Subscribers to shorten the duration of a synchronization being pulled from a Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="796e3-227">如果 -MaxDeliveredTransactions 和 -Continuous 都已指定，「散發代理程式」會傳遞指定的交易數目，然後停止 (即使已指定 -Continuous)。</span><span class="sxs-lookup"><span data-stu-id="796e3-227">If -MaxDeliveredTransactions and -Continuous are both specified, the Distribution Agent delivers the specified number of transactions and then stops (even though -Continuous is specified).</span></span> <span data-ttu-id="796e3-228">作業完成之後，您必須重新啟動「散發代理程式」。</span><span class="sxs-lookup"><span data-stu-id="796e3-228">You must restart the Distribution Agent after the job completes.</span></span>  
  
 <span data-ttu-id="796e3-229">**-MessageInterval**  _message_interval_</span><span class="sxs-lookup"><span data-stu-id="796e3-229">**-MessageInterval**  _message_interval_</span></span>  
 <span data-ttu-id="796e3-230">這是用於記錄的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="796e3-230">Is the time interval used for history logging.</span></span> <span data-ttu-id="796e3-231">到達下列其中一個參數時，系統就會記錄記錄事件：</span><span class="sxs-lookup"><span data-stu-id="796e3-231">A history event is logged when one of these parameters is reached:</span></span>  
  
-   <span data-ttu-id="796e3-232">記錄上一個歷程記錄事件之後，到達 **TransactionsPerHistory** 值。</span><span class="sxs-lookup"><span data-stu-id="796e3-232">The **TransactionsPerHistory** value is reached after the last history event is logged.</span></span>  
  
-   <span data-ttu-id="796e3-233">記錄上一個歷程記錄事件之後，到達 **MessageInterval** 值。</span><span class="sxs-lookup"><span data-stu-id="796e3-233">The **MessageInterval** value is reached after the last history event is logged.</span></span>  
  
 <span data-ttu-id="796e3-234">如果來源沒有任何複寫的交易可用，代理程式就會回報無交易訊息給散發者。</span><span class="sxs-lookup"><span data-stu-id="796e3-234">If there is no replicated transaction available at the source, the agent reports a no-transaction message to the Distributor.</span></span> <span data-ttu-id="796e3-235">這個選項會指定回報另一個無交易訊息之前等候的時間長度。</span><span class="sxs-lookup"><span data-stu-id="796e3-235">This option specifies how long the agent waits before reporting another no-transaction message.</span></span> <span data-ttu-id="796e3-236">在先前處理複寫的交易之後，當代理程式偵測到來源沒有任何交易可用時，代理程式一律會回報無交易訊息。</span><span class="sxs-lookup"><span data-stu-id="796e3-236">Agents always report a no-transaction message when they detect that there are no transactions available at the source after previously processing replicated transactions.</span></span> <span data-ttu-id="796e3-237">預設值是 60 秒。</span><span class="sxs-lookup"><span data-stu-id="796e3-237">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="796e3-238">**-OledbStreamThreshold** _oledb_stream_threshold_</span><span class="sxs-lookup"><span data-stu-id="796e3-238">**-OledbStreamThreshold** _oledb_stream_threshold_</span></span>  
 <span data-ttu-id="796e3-239">指定二進位大型物件資料 (其中資料將繫結為資料流) 的大小下限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="796e3-239">Specifies the minimum size, in bytes, for binary large object data above which the data will be bound as a stream.</span></span> <span data-ttu-id="796e3-240">您必須指定 **-UseOledbStreaming** 才能使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-240">You must specify **-UseOledbStreaming** to use this parameter.</span></span> <span data-ttu-id="796e3-241">值的範圍在 400 至 1048576 個位元組之間，預設為 16384 個位元組。</span><span class="sxs-lookup"><span data-stu-id="796e3-241">Values can range from 400 to 1048576 bytes, with a default of 16384 bytes.</span></span>  
  
 <span data-ttu-id="796e3-242">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="796e3-242">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="796e3-243">這是代理程式輸出檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="796e3-243">Is the path of the agent output file.</span></span> <span data-ttu-id="796e3-244">如果未提供檔案名稱，輸出將傳送至主控台。</span><span class="sxs-lookup"><span data-stu-id="796e3-244">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="796e3-245">如果指定的檔案名稱存在，輸出就會附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="796e3-245">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="796e3-246">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="796e3-246">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="796e3-247">指定輸出是否應該詳細。</span><span class="sxs-lookup"><span data-stu-id="796e3-247">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="796e3-248">如果詳細資訊層級為 0，系統就只會列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="796e3-248">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="796e3-249">如果詳細資訊層級為 1，系統就會列印所有進度報表訊息。</span><span class="sxs-lookup"><span data-stu-id="796e3-249">If the verbose level is **1**, all the progress report messages are printed.</span></span> <span data-ttu-id="796e3-250">如果詳細資訊層級為 2 (預設值)，系統就會列印所有錯誤訊息和進度報表訊息 (可用於偵錯)。</span><span class="sxs-lookup"><span data-stu-id="796e3-250">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="796e3-251">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="796e3-251">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="796e3-252">這是封包大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="796e3-252">Is the packet size, in bytes.</span></span> <span data-ttu-id="796e3-253">預設值是 4096 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="796e3-253">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="796e3-254">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="796e3-254">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="796e3-255">這是針對複寫交易查詢散發資料庫的頻率 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="796e3-255">Is how often, in seconds, the distribution database is queried for replicated transactions.</span></span> <span data-ttu-id="796e3-256">預設值是 5 秒。</span><span class="sxs-lookup"><span data-stu-id="796e3-256">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="796e3-257">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="796e3-257">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="796e3-258">指定要用於代理程式參數的代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="796e3-258">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="796e3-259">如果 **ProfileName** 為 NULL，就會停用代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="796e3-259">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="796e3-260">如果沒有指定 **ProfileName** ，就會使用該代理程式類型的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="796e3-260">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="796e3-261">如需資訊，請參閱[複寫代理程式設定檔](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="796e3-261">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="796e3-262">**-Publication**  _publication_</span><span class="sxs-lookup"><span data-stu-id="796e3-262">**-Publication**  _publication_</span></span>  
 <span data-ttu-id="796e3-263">這是發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-263">Is the name of the publication.</span></span> <span data-ttu-id="796e3-264">只有在發行集設定成隨時都有快照供新的訂閱或重新初始化的訂閱使用時，這個參數才有效。</span><span class="sxs-lookup"><span data-stu-id="796e3-264">This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.</span></span>  
  
 <span data-ttu-id="796e3-265">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="796e3-265">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="796e3-266">這是查詢逾時之前的秒數。預設值是 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="796e3-266">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="796e3-267">**-QuotedIdentifier** _quoted_identifier_</span><span class="sxs-lookup"><span data-stu-id="796e3-267">**-QuotedIdentifier** _quoted_identifier_</span></span>  
 <span data-ttu-id="796e3-268">指定要使用的引號識別碼字元。</span><span class="sxs-lookup"><span data-stu-id="796e3-268">Specifies the quoted identifier character to use.</span></span> <span data-ttu-id="796e3-269">此值的第一個字元表示散發代理程式所使用的值。</span><span class="sxs-lookup"><span data-stu-id="796e3-269">The first character of the value indicates the value the Distribution Agent uses.</span></span> <span data-ttu-id="796e3-270">如果使用了沒有任何值的 **QuotedIdentifier** ，散發代理程式就會使用空格。</span><span class="sxs-lookup"><span data-stu-id="796e3-270">If **QuotedIdentifier** is used with no value, the Distribution Agent uses a space.</span></span> <span data-ttu-id="796e3-271">如果未使用 **QuotedIdentifier** ，散發代理程式就會使用訂閱者所支援的任何引號識別項。</span><span class="sxs-lookup"><span data-stu-id="796e3-271">If **QuotedIdentifier** is not used, the Distribution Agent uses whatever quoted identifier the Subscriber supports.</span></span>  
  
 <span data-ttu-id="796e3-272">**-SkipErrors** _native_error_id_ [ **:** _...n_]</span><span class="sxs-lookup"><span data-stu-id="796e3-272">**-SkipErrors** _native_error_id_ [**:**_...n_]</span></span>  
 <span data-ttu-id="796e3-273">這是冒號分隔的清單，其中指定了這個代理程式要忽略的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="796e3-273">Is a colon-separated list that specifies the error numbers to be skipped by this agent.</span></span>  
  
 <span data-ttu-id="796e3-274">**-SubscriberDatabasePath** _subscriber_database_path_</span><span class="sxs-lookup"><span data-stu-id="796e3-274">**-SubscriberDatabasePath** _subscriber_database_path_</span></span>  
 <span data-ttu-id="796e3-275">如果 **SubscriberType** 是 **2** (允許連接至沒有 ODBC 資料來源名稱 (DSN) 的 Jet 資料庫)，這就是 Jet 資料庫 (.mdb 檔) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-275">Is the path to the Jet database (.mdb file) if **SubscriberType** is **2** (allows a connection to a Jet database without an ODBC Data Source Name (DSN)).</span></span>  
  
 <span data-ttu-id="796e3-276">**-SubscriberLogin** _subscriber_login_</span><span class="sxs-lookup"><span data-stu-id="796e3-276">**-SubscriberLogin** _subscriber_login_</span></span>  
 <span data-ttu-id="796e3-277">這是訂閱者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-277">Is the Subscriber login name.</span></span> <span data-ttu-id="796e3-278">如果 **SubscriberSecurityMode** 是 **0** (代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證)，您就必須指定這個參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-278">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="796e3-279">**-SubscriberPassword** _subscriber_password_</span><span class="sxs-lookup"><span data-stu-id="796e3-279">**-SubscriberPassword** _subscriber_password_</span></span>  
 <span data-ttu-id="796e3-280">這是訂閱者密碼。</span><span class="sxs-lookup"><span data-stu-id="796e3-280">Is the Subscriber password.</span></span> <span data-ttu-id="796e3-281">如果 **SubscriberSecurityMode** 是 **0** (代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證)，您就必須指定這個參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-281">If **SubscriberSecurityMode** is **0** (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication), this parameter must be specified.</span></span>  
  
 <span data-ttu-id="796e3-282">**-SubscriberSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="796e3-282">**-SubscriberSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="796e3-283">指定訂閱者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="796e3-283">Specifies the security mode of the Subscriber.</span></span> <span data-ttu-id="796e3-284">值為 0 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表示  驗證，而值為 1 則表示 Windows 驗證模式 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="796e3-284">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, and a value of **1** indicates Windows Authentication Mode (default).</span></span>  
  
 <span data-ttu-id="796e3-285">**-SubscriberType** [ **0**| **1**| **3**]</span><span class="sxs-lookup"><span data-stu-id="796e3-285">**-SubscriberType** [ **0**| **1**| **3**]</span></span>  
 <span data-ttu-id="796e3-286">指定由散發代理程式所使用的訂閱者連接類型。</span><span class="sxs-lookup"><span data-stu-id="796e3-286">Specifies the type of Subscriber connection used by the Distribution Agent.</span></span>  
  
|<span data-ttu-id="796e3-287">SubscriberType 值</span><span class="sxs-lookup"><span data-stu-id="796e3-287">SubscriberType value</span></span>|<span data-ttu-id="796e3-288">描述</span><span class="sxs-lookup"><span data-stu-id="796e3-288">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="796e3-289">**0**</span><span class="sxs-lookup"><span data-stu-id="796e3-289">**0**</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="796e3-290">**1**</span><span class="sxs-lookup"><span data-stu-id="796e3-290">**1**</span></span>|<span data-ttu-id="796e3-291">ODBC 資料來源</span><span class="sxs-lookup"><span data-stu-id="796e3-291">ODBC data source</span></span>|  
|<span data-ttu-id="796e3-292">**3**</span><span class="sxs-lookup"><span data-stu-id="796e3-292">**3**</span></span>|<span data-ttu-id="796e3-293">OLE DB 資料來源</span><span class="sxs-lookup"><span data-stu-id="796e3-293">OLE DB data source</span></span>|  
  
 <span data-ttu-id="796e3-294">**-SubscriptionStreams** [**0**|**1**|**2**|...**64**]</span><span class="sxs-lookup"><span data-stu-id="796e3-294">**-SubscriptionStreams** [**0**|**1**|**2**|...**64**]</span></span>  
 <span data-ttu-id="796e3-295">這是在維護許多使用單一執行緒時所提供的交易式特性時，每個散發代理程式可用來將變更批次並行套用在訂閱者上的連接數目。</span><span class="sxs-lookup"><span data-stu-id="796e3-295">Is the number of connections allowed per Distribution Agent to apply batches of changes in parallel to a Subscriber, while maintaining many of the transactional characteristics present when using a single thread.</span></span> <span data-ttu-id="796e3-296">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 若為  發行者，就支援範圍在 1 至 64 之間的值。</span><span class="sxs-lookup"><span data-stu-id="796e3-296">For a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, a range of values from 1 to 64 is supported.</span></span> <span data-ttu-id="796e3-297">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 只有當發行者或散發者在  或更新版本上執行時，才支援這個參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-297">This parameter is only supported when the Publisher and Distributor are running on [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later versions.</span></span> <span data-ttu-id="796e3-298">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 這個參數不支援非  訂閱者或點對點訂閱，否則就必須為 0。</span><span class="sxs-lookup"><span data-stu-id="796e3-298">This parameter is not supported or must be 0 for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers or peer-to-peer subscriptions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="796e3-299">如果有一個連接無法執行或認可，則所有連接都將中止目前批次，且代理程式將使用單一資料流重試失敗的批次。</span><span class="sxs-lookup"><span data-stu-id="796e3-299">If one of the connections fails to execute or commit, all connections will abort the current batch, and the agent will use a single stream to retry the failed batches.</span></span> <span data-ttu-id="796e3-300">在此重試階段完成之前，「訂閱者」端可能會出現暫時的交易不一致性。</span><span class="sxs-lookup"><span data-stu-id="796e3-300">Before this retry phase completes, there can be temporary transactional inconsistencies at the Subscriber.</span></span> <span data-ttu-id="796e3-301">成功認可失敗的批次後，「訂閱者」將返回交易一致性的狀態。</span><span class="sxs-lookup"><span data-stu-id="796e3-301">After the failed batches are successfully committed, the Subscriber is brought back to a state of transactional consistency.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="796e3-302">當您針對 **-SubscriptionStreams**指定 2 以上的值時，在訂閱者端收到交易的順序可能會與在發行者端建立交易的順序不同。</span><span class="sxs-lookup"><span data-stu-id="796e3-302">When you specify a value of 2 or greater for **-SubscriptionStreams**, the order in which transactions are received at the Subscriber may differ from the order in which they were made at the Publisher.</span></span> <span data-ttu-id="796e3-303">如果這個行為在同步處理期間導致條件約束違規，您就應該使用 NOT FOR REPLICATION 選項來停用同步處理期間的條件約束強制執行。</span><span class="sxs-lookup"><span data-stu-id="796e3-303">If this behavior causes constraint violations during synchronization, you should use the NOT FOR REPLICATION option to disable the enforcement of constraints during synchronization.</span></span> <span data-ttu-id="796e3-304">如需詳細資訊，請參閱[在同步處理期間控制觸發程序和條件約束的行為 &#40;複寫 Transact-SQL 程式設計&#41;](../control-behavior-of-triggers-and-constraints-in-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="796e3-304">For more information, see [Control the Behavior of Triggers and Constraints During Synchronization &#40;Replication Transact-SQL Programming&#41;](../control-behavior-of-triggers-and-constraints-in-synchronization.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="796e3-305">[!INCLUDE[tsql](../../../includes/tsql-md.md)]Subscriptionstreams 不適用於設定為傳遞  的發行項。</span><span class="sxs-lookup"><span data-stu-id="796e3-305">Subscriptionstreams do not work for articles configured to deliver [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="796e3-306">若要使用 subscriptionstreams，請改將發行項設定為傳遞預存程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="796e3-306">To use subscriptionstreams, configure articles to deliver stored procedure calls instead.</span></span>  
  
 <span data-ttu-id="796e3-307">**-SubscriptionTableName** _subscription_table_</span><span class="sxs-lookup"><span data-stu-id="796e3-307">**-SubscriptionTableName** _subscription_table_</span></span>  
 <span data-ttu-id="796e3-308">這是在給定訂閱者端產生或使用之訂閱資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="796e3-308">Is the name of the subscription table generated or used at the given Subscriber.</span></span> <span data-ttu-id="796e3-309">未指定時，會使用 [MSreplication_subscriptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql) 資料表。</span><span class="sxs-lookup"><span data-stu-id="796e3-309">When not specified, the [MSreplication_subscriptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql) table is used.</span></span> <span data-ttu-id="796e3-310">您可以針對不支援長檔名的資料庫管理系統 (DBMS) 使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="796e3-310">Use this option for database management systems (DBMS) that do not support long file names.</span></span>  
  
 <span data-ttu-id="796e3-311">**-SubscriptionType** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="796e3-311">**-SubscriptionType** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="796e3-312">指定散發的訂閱類型。</span><span class="sxs-lookup"><span data-stu-id="796e3-312">Specifies the subscription type for distribution.</span></span> <span data-ttu-id="796e3-313">值為 **0** 表示發送訂閱、值為 **1** 表示提取訂閱，而值為 2 則表示匿名訂閱。</span><span class="sxs-lookup"><span data-stu-id="796e3-313">A value of **0** indicates a push subscription, a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.</span></span>  
  
 <span data-ttu-id="796e3-314">**-TransactionsPerHistory** [ **0**| **1**|...**10000**]</span><span class="sxs-lookup"><span data-stu-id="796e3-314">**-TransactionsPerHistory** [ **0**| **1**|... **10000**]</span></span>  
 <span data-ttu-id="796e3-315">指定記錄作業的交易間隔。</span><span class="sxs-lookup"><span data-stu-id="796e3-315">Specifies the transaction interval for history logging.</span></span> <span data-ttu-id="796e3-316">如果上一個記錄執行個體之後認可的交易數目大於這個選項，系統就會記錄記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="796e3-316">If the number of committed transactions after the last instance of history logging is greater than this option, a history message is logged.</span></span> <span data-ttu-id="796e3-317">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="796e3-317">The default is 100.</span></span> <span data-ttu-id="796e3-318">**0** 值表示無限 **TransactionsPerHistory**。</span><span class="sxs-lookup"><span data-stu-id="796e3-318">A value of **0** indicates infinite **TransactionsPerHistory**.</span></span> <span data-ttu-id="796e3-319">請參閱前面的 **-MessageInterval**參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-319">See the preceding **-MessageInterval**parameter.</span></span>  
  
 <span data-ttu-id="796e3-320">**-UseDTS**</span><span class="sxs-lookup"><span data-stu-id="796e3-320">**-UseDTS**</span></span>  
 <span data-ttu-id="796e3-321">必須針對允許資料轉換的發行集指定為參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-321">Must be specified as a parameter for a publication that allows data transformation.</span></span>  
  
 <span data-ttu-id="796e3-322">**-UseInprocLoader**</span><span class="sxs-lookup"><span data-stu-id="796e3-322">**-UseInprocLoader**</span></span>  
 <span data-ttu-id="796e3-323">將快照集檔案套用至訂閱者時，讓散發代理程式使用 BULK INSERT 命令，藉以改善初始快照集的效能。</span><span class="sxs-lookup"><span data-stu-id="796e3-323">Improves the performance of the initial snapshot by causing the Distribution Agent to use the BULK INSERT command when applying snapshot files to the Subscriber.</span></span> <span data-ttu-id="796e3-324">這個參數已被取代，因為它與 XML 資料類型不相容。</span><span class="sxs-lookup"><span data-stu-id="796e3-324">This parameter is deprecated because it is not compatible with the XML data type.</span></span> <span data-ttu-id="796e3-325">如果您不複寫 XML 資料，則可使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-325">If you are not replicating XML data, this parameter can be used.</span></span> <span data-ttu-id="796e3-326">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 這個參數無法搭配字元模式快照集或非  訂閱者使用。</span><span class="sxs-lookup"><span data-stu-id="796e3-326">This parameter cannot be used with character mode snapshots or non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers.</span></span> <span data-ttu-id="796e3-327">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果您使用這個參數，位於訂閱者端的  服務帳戶就必須擁有快照集 .bcp 資料檔案所在目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="796e3-327">If you use this parameter, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located.</span></span> <span data-ttu-id="796e3-328">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 沒有使用這個參數時，代理程式 (代表非 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者) 或代理程式所載入的 ODBC 驅動程式 (代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者) 就會從這些檔案中讀取，因此不會使用  服務帳戶的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="796e3-328">When this parameter is not used, the agent (for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers) or the ODBC driver loaded by the agent (for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers) reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is not used.</span></span>  
  
 <span data-ttu-id="796e3-329">**-UseOledbStreaming**</span><span class="sxs-lookup"><span data-stu-id="796e3-329">**-UseOledbStreaming**</span></span>  
 <span data-ttu-id="796e3-330">指定這個參數時，可將二進位大型物件資料繫結成資料流。</span><span class="sxs-lookup"><span data-stu-id="796e3-330">When specified, enables the binding of binary large object data as a stream.</span></span> <span data-ttu-id="796e3-331">您可以使用 **-OledbStreamThreshold** 來指定將使用的資料流大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="796e3-331">Use **-OledbStreamThreshold** to specify the size, in bytes, above which a stream will be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="796e3-332">備註</span><span class="sxs-lookup"><span data-stu-id="796e3-332">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="796e3-333">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果您已將  Agent 安裝成在本機系統帳戶而非網域使用者帳戶 (預設值) 底下執行，這項服務就只能存取本機電腦。</span><span class="sxs-lookup"><span data-stu-id="796e3-333">If you have installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account rather than under a domain user account (the default), the service can only access the local computer.</span></span> <span data-ttu-id="796e3-334">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如果在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Agent 底下執行的散發代理程式設定為使用 Windows 驗證模式，當它登入  執行個體時，散發代理程式就會失敗。</span><span class="sxs-lookup"><span data-stu-id="796e3-334">If the Distribution Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Distribution Agent fails.</span></span> <span data-ttu-id="796e3-335">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設設定為  驗證。</span><span class="sxs-lookup"><span data-stu-id="796e3-335">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="796e3-336">[View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)如需有關變更安全性帳戶的詳細資訊，請參閱＜＞。</span><span class="sxs-lookup"><span data-stu-id="796e3-336">For information on changing security accounts, see [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="796e3-337">若要啟動散發代理程式，請從命令提示字元執行 **distrib.exe** 。</span><span class="sxs-lookup"><span data-stu-id="796e3-337">To start the Distribution Agent, execute **distrib.exe** from the command prompt.</span></span> <span data-ttu-id="796e3-338">如需詳細資訊，請參閱[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="796e3-338">For information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="796e3-339">變更記錄</span><span class="sxs-lookup"><span data-stu-id="796e3-339">Change History</span></span>  
  
|<span data-ttu-id="796e3-340">更新的內容</span><span class="sxs-lookup"><span data-stu-id="796e3-340">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="796e3-341"> 已加入 -ExtendedEventConfigFile 參數。</span><span class="sxs-lookup"><span data-stu-id="796e3-341">Added the **-ExtendedEventConfigFile** parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="796e3-342">另請參閱</span><span class="sxs-lookup"><span data-stu-id="796e3-342">See Also</span></span>  
 [<span data-ttu-id="796e3-343">複寫代理程式管理</span><span class="sxs-lookup"><span data-stu-id="796e3-343">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
