---
title: 複寫記錄讀取器代理程式 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, executables
- Log Reader Agent, parameter reference
- agents [SQL Server replication], Log Reader Agent
- command prompt [SQL Server replication]
ms.assetid: 5487b645-d99b-454c-8bd2-aff470709a0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 120c7418d8b16fe6d083961affcf0b8a9c9f6c65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595922"
---
# <a name="replication-log-reader-agent"></a><span data-ttu-id="92f3e-102">複寫記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="92f3e-102">Replication Log Reader Agent</span></span>
  <span data-ttu-id="92f3e-103">「複寫記錄讀取器代理程式」是一個可執行檔，它會監視針對異動複寫所設定之每個資料庫的交易記錄，並將標示要複寫的交易從交易記錄複製到散發資料庫中。</span><span class="sxs-lookup"><span data-stu-id="92f3e-103">The Replication Log Reader Agent is an executable that monitors the transaction log of each database configured for transactional replication and copies the transactions marked for replication from the transaction log into the distribution database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92f3e-104">您可以使用任何順序來指定參數。</span><span class="sxs-lookup"><span data-stu-id="92f3e-104">Parameters can be specified in any order.</span></span> <span data-ttu-id="92f3e-105">沒有指定選擇性參數時，系統就會使用以預設代理程式設定檔為基礎的預先定義值。</span><span class="sxs-lookup"><span data-stu-id="92f3e-105">When optional parameters are not specified, predefined values based on the default agent profile are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f3e-106">語法</span><span class="sxs-lookup"><span data-stu-id="92f3e-106">Syntax</span></span>  
  
```  
  
      logread [-?]   
-Publisherserver_name[\instance_name]   
-PublisherDBpublisher_database   
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-HistoryVerboseLevel [0|1|2]]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-LogScanThresholdscan_threshold]  
[-MaxCmdsInTrannumber_of_commands]  
[-MessageIntervalmessage_interval]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2|3|4]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]   
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherSecurityMode [0|1]]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-QueryTimeOutquery_time_out_seconds]  
[-ReadBatchSizenumber_of_transactions]   
[-ReadBatchThresholdread_batch_threshold]  
[-RecoverFromDataErrors]  
```  
  
## <a name="arguments"></a><span data-ttu-id="92f3e-107">引數</span><span class="sxs-lookup"><span data-stu-id="92f3e-107">Arguments</span></span>  
 <span data-ttu-id="92f3e-108">**-?**</span><span class="sxs-lookup"><span data-stu-id="92f3e-108">**-?**</span></span>  
 <span data-ttu-id="92f3e-109">顯示使用資訊。</span><span class="sxs-lookup"><span data-stu-id="92f3e-109">Displays usage information.</span></span>  
  
 <span data-ttu-id="92f3e-110">**-Publisher** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="92f3e-110">**-Publisher** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="92f3e-111">這是發行者的名稱。</span><span class="sxs-lookup"><span data-stu-id="92f3e-111">Is the name of the Publisher.</span></span> <span data-ttu-id="92f3e-112">請針對該伺服器上的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 *server_name*。</span><span class="sxs-lookup"><span data-stu-id="92f3e-112">Specify *server_name* for the default instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="92f3e-113">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="92f3e-113">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="92f3e-114">**-PublisherDB** _publisher_database_</span><span class="sxs-lookup"><span data-stu-id="92f3e-114">**-PublisherDB** _publisher_database_</span></span>  
 <span data-ttu-id="92f3e-115">這是發行者資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="92f3e-115">Is the name of the Publisher database.</span></span>  
  
 <span data-ttu-id="92f3e-116">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="92f3e-116">**-Continuous**</span></span>  
 <span data-ttu-id="92f3e-117">指定代理程式是否會嘗試持續輪詢複寫的交易。</span><span class="sxs-lookup"><span data-stu-id="92f3e-117">Specifies whether the agent tries to poll replicated transactions continually.</span></span> <span data-ttu-id="92f3e-118">如果您指定了這個參數，代理程式就會以輪詢間隔輪詢來源的複寫交易，即使沒有任何交易暫止也一樣。</span><span class="sxs-lookup"><span data-stu-id="92f3e-118">If specified, the agent polls replicated transactions from the source at polling intervals even if there are no transactions pending.</span></span>  
  
 <span data-ttu-id="92f3e-119">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="92f3e-119">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="92f3e-120">這是代理程式定義檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="92f3e-120">Is the path of the agent definition file.</span></span> <span data-ttu-id="92f3e-121">代理程式定義檔包含代理程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="92f3e-121">An agent definition file contains command-line arguments for the agent.</span></span> <span data-ttu-id="92f3e-122">此檔案的內容會剖析為可執行檔。</span><span class="sxs-lookup"><span data-stu-id="92f3e-122">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="92f3e-123">請使用雙引號 (") 來指定包含任意字元的引數值。</span><span class="sxs-lookup"><span data-stu-id="92f3e-123">Use double quotation marks (") to specify argument values that contain arbitrary characters.</span></span>  
  
 <span data-ttu-id="92f3e-124">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="92f3e-124">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="92f3e-125">這是散發者的名稱。</span><span class="sxs-lookup"><span data-stu-id="92f3e-125">Is the Distributor name.</span></span> <span data-ttu-id="92f3e-126">請針對該伺服器上的 *預設執行個體指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="92f3e-126">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="92f3e-127">請針對該伺服器上 _server_name_ **\\** _instance_name_ instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體指定 server_name。</span><span class="sxs-lookup"><span data-stu-id="92f3e-127">Specify _server_name_**\\**_instance_name_ for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span>  
  
 <span data-ttu-id="92f3e-128">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="92f3e-128">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="92f3e-129">這是散發者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="92f3e-129">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="92f3e-130">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="92f3e-130">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="92f3e-131">這是散發者密碼。</span><span class="sxs-lookup"><span data-stu-id="92f3e-131">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="92f3e-132">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="92f3e-132">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="92f3e-133">指定散發者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="92f3e-133">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="92f3e-134">值為 **0** 表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證模式 (預設值)，而值為 **1** 則表示 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="92f3e-134">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="92f3e-135">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="92f3e-135">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="92f3e-136">這是建立連接時，記錄讀取器代理程式所使用的安全通訊端層 (SSL) 加密層級。</span><span class="sxs-lookup"><span data-stu-id="92f3e-136">Is the level of Secure Sockets Layer (SSL) encryption that is used by the Log Reader Agent when making connections.</span></span>  
  
|<span data-ttu-id="92f3e-137">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="92f3e-137">EncryptionLevel value</span></span>|<span data-ttu-id="92f3e-138">描述</span><span class="sxs-lookup"><span data-stu-id="92f3e-138">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="92f3e-139">**0**</span><span class="sxs-lookup"><span data-stu-id="92f3e-139">**0**</span></span>|<span data-ttu-id="92f3e-140">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="92f3e-140">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="92f3e-141">**1**</span><span class="sxs-lookup"><span data-stu-id="92f3e-141">**1**</span></span>|<span data-ttu-id="92f3e-142">指定要使用 SSL，但是代理程式不會驗證 SSL 伺服器憑證是否由受信任的簽發者簽署。</span><span class="sxs-lookup"><span data-stu-id="92f3e-142">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="92f3e-143">**2**</span><span class="sxs-lookup"><span data-stu-id="92f3e-143">**2**</span></span>|<span data-ttu-id="92f3e-144">指定要使用 SSL，而且憑證會經過驗證。</span><span class="sxs-lookup"><span data-stu-id="92f3e-144">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="92f3e-145">定義的 SSL 憑證必須包含 SQL Server 的完整網域名稱才會有效。</span><span class="sxs-lookup"><span data-stu-id="92f3e-145">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="92f3e-146">為了讓代理程式能在將 -EncryptionLevel 設定為 2 時成功連線，請在本機 SQL Server 上建立別名。</span><span class="sxs-lookup"><span data-stu-id="92f3e-146">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="92f3e-147">'Alias Name' 參數應為伺服器名稱，且應將 'Server' 參數設為 SQL Server 的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="92f3e-147">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
 
 <span data-ttu-id="92f3e-148">如需詳細資訊，請參閱[SQL Server 複寫安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="92f3e-148">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="92f3e-149">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="92f3e-149">**-ExtendedEventConfigFile** _configuration_path_and_file_name_</span></span>  
 <span data-ttu-id="92f3e-150">指定擴充的事件 XML 組態檔的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="92f3e-150">Specifies the path and file name for the extended events XML configuration file.</span></span> <span data-ttu-id="92f3e-151">擴充的事件組態檔可讓您設定工作階段以及啟用事件追蹤。</span><span class="sxs-lookup"><span data-stu-id="92f3e-151">The extended events configuration file allows you to configure sessions and enable events for tracking.</span></span>  
  
 <span data-ttu-id="92f3e-152">**-HistoryVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="92f3e-152">**-HistoryVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="92f3e-153">指定在記錄讀取器作業期間記錄的記錄量。</span><span class="sxs-lookup"><span data-stu-id="92f3e-153">Specifies the amount of history logged during a log reader operation.</span></span> <span data-ttu-id="92f3e-154">您可以透過選取 1，盡量減少記錄作業的效能影響。</span><span class="sxs-lookup"><span data-stu-id="92f3e-154">You can minimize the performance effect of history logging by selecting **1**.</span></span>  
  
|<span data-ttu-id="92f3e-155">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="92f3e-155">HistoryVerboseLevel value</span></span>|<span data-ttu-id="92f3e-156">描述</span><span class="sxs-lookup"><span data-stu-id="92f3e-156">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="92f3e-157">**0**</span><span class="sxs-lookup"><span data-stu-id="92f3e-157">**0**</span></span>||  
|<span data-ttu-id="92f3e-158">**1**</span><span class="sxs-lookup"><span data-stu-id="92f3e-158">**1**</span></span>|<span data-ttu-id="92f3e-159">預設值。</span><span class="sxs-lookup"><span data-stu-id="92f3e-159">Default.</span></span> <span data-ttu-id="92f3e-160">一律更新相同狀態的上一個記錄訊息 (啟動、進度、成功等等)。</span><span class="sxs-lookup"><span data-stu-id="92f3e-160">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="92f3e-161">如果沒有任何具有相同狀態的上一筆記錄存在，便插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="92f3e-161">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="92f3e-162">**2**</span><span class="sxs-lookup"><span data-stu-id="92f3e-162">**2**</span></span>|<span data-ttu-id="92f3e-163">除非記錄用於閒置訊息或長時間執行作業訊息等事件 (在此情況下，更新之前的記錄)，否則便插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="92f3e-163">Insert new history records unless the record is for such things as idle messages or long-running job messages, in which case update the previous records.</span></span>|  
  
 <span data-ttu-id="92f3e-164">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span><span class="sxs-lookup"><span data-stu-id="92f3e-164">**-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_</span></span>  
 <span data-ttu-id="92f3e-165">這是記錄執行緒檢查是否有任何現有的連接正在等候伺服器回應之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="92f3e-165">Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server.</span></span> <span data-ttu-id="92f3e-166">執行長時間執行的批次時，您可以減少這個值，避免檢查代理程式將記錄讀取器代理程式標示為有疑問。</span><span class="sxs-lookup"><span data-stu-id="92f3e-166">This value can be decreased to avoid having the checkup agent mark the Log Reader Agent as suspect when executing a long-running batch.</span></span> <span data-ttu-id="92f3e-167">預設為 300 秒。</span><span class="sxs-lookup"><span data-stu-id="92f3e-167">The default is 300 seconds.</span></span>  
  
 <span data-ttu-id="92f3e-168">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="92f3e-168">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="92f3e-169">這是登入逾時之前的秒數。預設為 15 秒。</span><span class="sxs-lookup"><span data-stu-id="92f3e-169">Is the number of seconds before the login times out. The default is 15 seconds.</span></span>  
  
 <span data-ttu-id="92f3e-170">**-LogScanThreshold** _scan_threshold_</span><span class="sxs-lookup"><span data-stu-id="92f3e-170">**-LogScanThreshold** _scan_threshold_</span></span>  
 <span data-ttu-id="92f3e-171">僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="92f3e-171">Internal use only.</span></span>  
  
 <span data-ttu-id="92f3e-172">**-MaxCmdsInTran** _number_of_commands_</span><span class="sxs-lookup"><span data-stu-id="92f3e-172">**-MaxCmdsInTran** _number_of_commands_</span></span>  
 <span data-ttu-id="92f3e-173">指定當記錄讀取器將命令寫入散發資料庫時，分組到某交易內的最大陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="92f3e-173">Specifies the maximum number of statements grouped into a transaction as the Log Reader writes commands to the distribution database.</span></span> <span data-ttu-id="92f3e-174">使用此參數可讓記錄讀取器代理程式和散發代理程式在「訂閱者」端套用命令時，於「發行者」端將大型交易 (由許多命令組成) 分割成幾個較小的交易。</span><span class="sxs-lookup"><span data-stu-id="92f3e-174">Using this parameter allows the Log Reader Agent and Distribution Agent to divide large transactions (consisting of many commands) at the Publisher into several smaller transactions when applied at the Subscriber.</span></span> <span data-ttu-id="92f3e-175">指定此參數可以降低「散發者」的競爭，並減少「發行者」和「訂閱者」之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="92f3e-175">Specifying this parameter can reduce contention at the Distributor and reduce latency between the Publisher and Subscriber.</span></span> <span data-ttu-id="92f3e-176">因為原始交易是以較小的單位來套用，所以「訂閱者」在原始交易結束之前可以存取大量的邏輯「發行者」交易資料列，打破了嚴格的交易不可部份完成性。</span><span class="sxs-lookup"><span data-stu-id="92f3e-176">Because the original transaction is applied in smaller units, the Subscriber can access rows of a large logical Publisher transaction prior to the end of the original transaction, breaking strict transactional atomicity.</span></span> <span data-ttu-id="92f3e-177">預設值為 **0**，保留「發行者」的交易界限。</span><span class="sxs-lookup"><span data-stu-id="92f3e-177">The default is **0**, which preserves the transaction boundaries of the Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92f3e-178">非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行集會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="92f3e-178">This parameter is ignored for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] publications.</span></span> <span data-ttu-id="92f3e-179">如需詳細資訊，請參閱＜ [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md)＞中的「設定交易集作業」一節。</span><span class="sxs-lookup"><span data-stu-id="92f3e-179">For more information, see the section "Configuring the Transaction Set Job" in [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).</span></span>  
  
 <span data-ttu-id="92f3e-180">**-MessageInterval** _message_interval_</span><span class="sxs-lookup"><span data-stu-id="92f3e-180">**-MessageInterval** _message_interval_</span></span>  
 <span data-ttu-id="92f3e-181">這是用於記錄的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="92f3e-181">Is the time interval used for history logging.</span></span> <span data-ttu-id="92f3e-182">在記錄上一個記錄事件之後，如果到達 **MessageInterval** 值，系統就會記錄記錄事件。</span><span class="sxs-lookup"><span data-stu-id="92f3e-182">A history event is logged when the **MessageInterval** value is reached after the last history event is logged.</span></span>  
  
 <span data-ttu-id="92f3e-183">如果來源沒有任何複寫的交易可用，代理程式就會回報無交易訊息給散發者。</span><span class="sxs-lookup"><span data-stu-id="92f3e-183">If there is no replicated transaction available at the source, the agent reports a no-transaction message to the Distributor.</span></span> <span data-ttu-id="92f3e-184">這個選項會指定回報另一個無交易訊息之前等候的時間長度。</span><span class="sxs-lookup"><span data-stu-id="92f3e-184">This option specifies how long the agent waits before reporting another no-transaction message.</span></span> <span data-ttu-id="92f3e-185">在先前處理複寫的交易之後，當代理程式偵測到來源沒有任何交易可用時，代理程式一律會回報無交易訊息。</span><span class="sxs-lookup"><span data-stu-id="92f3e-185">Agents always report a no-transaction message when they detect that there are no transactions available at the source after previously processing replicated transactions.</span></span> <span data-ttu-id="92f3e-186">預設值是 60 秒。</span><span class="sxs-lookup"><span data-stu-id="92f3e-186">The default is 60 seconds.</span></span>  
  
 <span data-ttu-id="92f3e-187">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="92f3e-187">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="92f3e-188">這是代理程式輸出檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="92f3e-188">Is the path of the agent output file.</span></span> <span data-ttu-id="92f3e-189">如果未提供檔案名稱，輸出將傳送至主控台。</span><span class="sxs-lookup"><span data-stu-id="92f3e-189">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="92f3e-190">如果指定的檔案名稱存在，輸出就會附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="92f3e-190">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="92f3e-191">**-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]</span><span class="sxs-lookup"><span data-stu-id="92f3e-191">**-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]</span></span>  
 <span data-ttu-id="92f3e-192">指定輸出是否應該詳細。</span><span class="sxs-lookup"><span data-stu-id="92f3e-192">Specifies whether the output should be verbose.</span></span>  
  
|<span data-ttu-id="92f3e-193">值</span><span class="sxs-lookup"><span data-stu-id="92f3e-193">Value</span></span>|<span data-ttu-id="92f3e-194">描述</span><span class="sxs-lookup"><span data-stu-id="92f3e-194">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92f3e-195">**0**</span><span class="sxs-lookup"><span data-stu-id="92f3e-195">**0**</span></span>|<span data-ttu-id="92f3e-196">僅列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="92f3e-196">Only error messages are printed.</span></span>|  
|<span data-ttu-id="92f3e-197">**1**</span><span class="sxs-lookup"><span data-stu-id="92f3e-197">**1**</span></span>|<span data-ttu-id="92f3e-198">列印所有代理程式進度報表訊息。</span><span class="sxs-lookup"><span data-stu-id="92f3e-198">All agent progress report messages are printed.</span></span>|  
|<span data-ttu-id="92f3e-199">**2** (預設值)</span><span class="sxs-lookup"><span data-stu-id="92f3e-199">**2** (default)</span></span>|<span data-ttu-id="92f3e-200">列印所有錯誤訊息和代理程式進度報表訊息。</span><span class="sxs-lookup"><span data-stu-id="92f3e-200">All error messages and agent progress report messages are printed.</span></span>|  
|<span data-ttu-id="92f3e-201">**3**</span><span class="sxs-lookup"><span data-stu-id="92f3e-201">**3**</span></span>|<span data-ttu-id="92f3e-202">列印每個複寫命令中的前 100 個位元組。</span><span class="sxs-lookup"><span data-stu-id="92f3e-202">The first 100 bytes of each replicated command are printed.</span></span>|  
|<span data-ttu-id="92f3e-203">**4**</span><span class="sxs-lookup"><span data-stu-id="92f3e-203">**4**</span></span>|<span data-ttu-id="92f3e-204">列印所有複寫指令。</span><span class="sxs-lookup"><span data-stu-id="92f3e-204">All replicated commands are printed.</span></span>|  
  
 <span data-ttu-id="92f3e-205">進行偵錯時，值 2-4 很有用。</span><span class="sxs-lookup"><span data-stu-id="92f3e-205">Values 2-4 are useful when debugging.</span></span>  
  
 <span data-ttu-id="92f3e-206">**-PacketSize** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="92f3e-206">**-PacketSize** _packet_size_</span></span>  
 <span data-ttu-id="92f3e-207">這是封包大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="92f3e-207">Is the packet size, in bytes.</span></span> <span data-ttu-id="92f3e-208">預設值是 4096 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="92f3e-208">The default is 4096 (bytes).</span></span>  
  
 <span data-ttu-id="92f3e-209">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="92f3e-209">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="92f3e-210">這是針對複寫交易查詢記錄的頻率 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="92f3e-210">Is how often, in seconds, the log is queried for replicated transactions.</span></span> <span data-ttu-id="92f3e-211">預設值是 5 秒。</span><span class="sxs-lookup"><span data-stu-id="92f3e-211">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="92f3e-212">**-ProfileName** _profile_name_</span><span class="sxs-lookup"><span data-stu-id="92f3e-212">**-ProfileName** _profile_name_</span></span>  
 <span data-ttu-id="92f3e-213">指定要用於代理程式參數的代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="92f3e-213">Specifies an agent profile to use for agent parameters.</span></span> <span data-ttu-id="92f3e-214">如果 **ProfileName** 為 NULL，就會停用代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="92f3e-214">If **ProfileName** is NULL, the agent profile is disabled.</span></span> <span data-ttu-id="92f3e-215">如果沒有指定 **ProfileName** ，就會使用該代理程式類型的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="92f3e-215">If **ProfileName** is not specified, the default profile for the agent type is used.</span></span> <span data-ttu-id="92f3e-216">如需資訊，請參閱[複寫代理程式設定檔](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="92f3e-216">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="92f3e-217">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="92f3e-217">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="92f3e-218">指定參與具有發行集資料庫之資料庫鏡像工作階段的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉夥伴執行個體。</span><span class="sxs-lookup"><span data-stu-id="92f3e-218">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="92f3e-219">如需詳細資訊，請參閱 [資料庫鏡像和複寫 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="92f3e-219">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="92f3e-220">**-PublisherSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="92f3e-220">**-PublisherSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="92f3e-221">指定發行者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="92f3e-221">Specifies the security mode of the Publisher.</span></span> <span data-ttu-id="92f3e-222">值為 **0** 表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證 (預設值)，而值為 **1** 則表示 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="92f3e-222">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="92f3e-223">**-PublisherLogin** _publisher_login_</span><span class="sxs-lookup"><span data-stu-id="92f3e-223">**-PublisherLogin** _publisher_login_</span></span>  
 <span data-ttu-id="92f3e-224">這是發行者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="92f3e-224">Is the Publisher login name.</span></span>  
  
 <span data-ttu-id="92f3e-225">**-PublisherPassword** _publisher_password_</span><span class="sxs-lookup"><span data-stu-id="92f3e-225">**-PublisherPassword** _publisher_password_</span></span>  
 <span data-ttu-id="92f3e-226">這是發行者密碼。</span><span class="sxs-lookup"><span data-stu-id="92f3e-226">Is the Publisher password.</span></span>  
  
 <span data-ttu-id="92f3e-227">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="92f3e-227">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="92f3e-228">這是查詢逾時之前的秒數。預設值是 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="92f3e-228">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="92f3e-229">**-ReadBatchSize** _number_of_transactions_</span><span class="sxs-lookup"><span data-stu-id="92f3e-229">**-ReadBatchSize** _number_of_transactions_</span></span>  
 <span data-ttu-id="92f3e-230">這是每個處理循環中從發行資料庫之交易記錄讀取出的最大交易數目，預設值為 500。</span><span class="sxs-lookup"><span data-stu-id="92f3e-230">Is the maximum number of transactions read out of the transaction log of the publishing database per processing cycle, with a default of 500.</span></span> <span data-ttu-id="92f3e-231">代理程式將繼續以批次方式讀取交易，直到從記錄中讀取所有交易為止。</span><span class="sxs-lookup"><span data-stu-id="92f3e-231">The agent will continue to read transactions in batches until all transactions are read from the log.</span></span> <span data-ttu-id="92f3e-232">這個參數不支援 Oracle 發行者。</span><span class="sxs-lookup"><span data-stu-id="92f3e-232">This parameter is not supported for Oracle Publishers.</span></span>  
  
 <span data-ttu-id="92f3e-233">**-ReadBatchThreshold** _number_of_commands_</span><span class="sxs-lookup"><span data-stu-id="92f3e-233">**-ReadBatchThreshold** _number_of_commands_</span></span>  
 <span data-ttu-id="92f3e-234">這是要從交易記錄中讀取的複寫命令數目，然後散發代理程式便將這些命令發送至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="92f3e-234">Is the number of replication commands to be read from the transaction log before being issued to the Subscriber by the Distribution Agent.</span></span> <span data-ttu-id="92f3e-235">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="92f3e-235">The default is 0.</span></span> <span data-ttu-id="92f3e-236">如果沒有指定這個參數，記錄讀取器代理程式將讀取至記錄結尾或 **-ReadBatchSize** (交易數目) 中指定的數目。</span><span class="sxs-lookup"><span data-stu-id="92f3e-236">If this parameter is not specified, the Log Reader Agent will read to the end of the log or to the number specified in **-ReadBatchSize** (number of transactions).</span></span>  
  
 <span data-ttu-id="92f3e-237">**-RecoverFromDataErrors**</span><span class="sxs-lookup"><span data-stu-id="92f3e-237">**-RecoverFromDataErrors**</span></span>  
 <span data-ttu-id="92f3e-238">指定當記錄讀取器代理程式在非 SQL Server 發行者發行的資料行資料中遇到錯誤時，它會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="92f3e-238">Specifies that the Log Reader Agent continue to run when it encounters errors in column data published from a non-SQL Server Publisher.</span></span> <span data-ttu-id="92f3e-239">根據預設，這類錯誤會導致記錄讀取器代理程式失敗。</span><span class="sxs-lookup"><span data-stu-id="92f3e-239">By default, such errors cause the Log Reader Agent to fail.</span></span> <span data-ttu-id="92f3e-240">當您使用 **-RecoverFromDataErrors**時，錯誤的資料行資料就會複寫成 NULL 或適當的非 Null 值，而且系統會在 [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) 資料表中記錄警告訊息。</span><span class="sxs-lookup"><span data-stu-id="92f3e-240">When you use **-RecoverFromDataErrors**, erroneous column data is replicated either as NULL or an appropriate nonnull value, and warning messages are logged to the [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) table.</span></span> <span data-ttu-id="92f3e-241">這個參數僅支援 Oracle 發行者。</span><span class="sxs-lookup"><span data-stu-id="92f3e-241">This parameter is only supported for Oracle Publishers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92f3e-242">備註</span><span class="sxs-lookup"><span data-stu-id="92f3e-242">Remarks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="92f3e-243">如果您將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 安裝成在本機系統帳戶而非網域使用者帳戶 (預設值) 底下執行，這項服務就只能存取本機電腦。</span><span class="sxs-lookup"><span data-stu-id="92f3e-243">If you installed [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to run under a local system account instead of under a domain user account (the default), the service can access only the local computer.</span></span> <span data-ttu-id="92f3e-244">如果在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 底下執行的記錄讀取器代理程式設定為使用 Windows 驗證模式，當它登入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]時，記錄讀取器代理程式就會失敗。</span><span class="sxs-lookup"><span data-stu-id="92f3e-244">If the Log Reader Agent that runs under [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the Log Reader Agent fails.</span></span> <span data-ttu-id="92f3e-245">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設設定為  驗證。</span><span class="sxs-lookup"><span data-stu-id="92f3e-245">The default setting is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="92f3e-246">如需有關變更安全性帳戶的詳細資訊，請參閱＜ [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)＞。</span><span class="sxs-lookup"><span data-stu-id="92f3e-246">For information about changing security accounts, see [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="92f3e-247">若要啟動記錄讀取器代理程式，請從命令提示字元執行 **logread.exe** 。</span><span class="sxs-lookup"><span data-stu-id="92f3e-247">To start the Log Reader Agent, execute **logread.exe** from the command prompt.</span></span> <span data-ttu-id="92f3e-248">如需詳細資訊，請參閱[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="92f3e-248">For information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="92f3e-249">變更記錄</span><span class="sxs-lookup"><span data-stu-id="92f3e-249">Change History</span></span>  
  
|<span data-ttu-id="92f3e-250">更新的內容</span><span class="sxs-lookup"><span data-stu-id="92f3e-250">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="92f3e-251"> 已加入 -ExtendedEventConfigFile 參數。</span><span class="sxs-lookup"><span data-stu-id="92f3e-251">Added the **-ExtendedEventConfigFile** parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92f3e-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92f3e-252">See Also</span></span>  
 [<span data-ttu-id="92f3e-253">複寫代理程式管理</span><span class="sxs-lookup"><span data-stu-id="92f3e-253">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
