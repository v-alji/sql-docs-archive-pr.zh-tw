---
title: 複寫佇列讀取器代理程式 | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 854c425db3fbaa346dab5eb2c41bd58cf03f65c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585900"
---
# <a name="replication-queue-reader-agent"></a><span data-ttu-id="25294-102">複寫佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="25294-102">Replication Queue Reader Agent</span></span>
  <span data-ttu-id="25294-103">「複寫佇列讀取器代理程式」是一個可執行檔，其會讀取儲存在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 佇列或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 訊息佇列中的訊息，然後將這些訊息套用至發行者。</span><span class="sxs-lookup"><span data-stu-id="25294-103">The Replication Queue Reader Agent is an executable that reads messages stored in a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] queue or a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Message Queue and then applies those messages to the Publisher.</span></span> <span data-ttu-id="25294-104">佇列讀取器代理程式可搭配允許佇列更新的快照式和交易式發行集使用。</span><span class="sxs-lookup"><span data-stu-id="25294-104">Queue Reader Agent is used with snapshot and transactional publications that allow queued updating.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25294-105">您可以使用任何順序來指定參數。</span><span class="sxs-lookup"><span data-stu-id="25294-105">Parameters can be specified in any order.</span></span> <span data-ttu-id="25294-106">沒有指定選擇性參數時，系統就會使用以預設代理程式設定檔為基礎的預先定義值。</span><span class="sxs-lookup"><span data-stu-id="25294-106">When optional parameters are not specified, predefined values based on the default agent profile are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25294-107">語法</span><span class="sxs-lookup"><span data-stu-id="25294-107">Syntax</span></span>  
  
```  
  
      qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFiledefinition_file]  
[-Distributorserver_name[\instance_name]]  
[-DistributionDBdistribution_database]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOutlogin_time_out_seconds]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingIntervalpolling_interval]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-ProfileNameagent_profile_name]  
[-QueryTimeOutquery_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="25294-108">引數</span><span class="sxs-lookup"><span data-stu-id="25294-108">Arguments</span></span>  
 <span data-ttu-id="25294-109">**-?**</span><span class="sxs-lookup"><span data-stu-id="25294-109">**-?**</span></span>  
 <span data-ttu-id="25294-110">顯示使用資訊。</span><span class="sxs-lookup"><span data-stu-id="25294-110">Displays usage information.</span></span>  
  
 <span data-ttu-id="25294-111">**-Continuous**</span><span class="sxs-lookup"><span data-stu-id="25294-111">**-Continuous**</span></span>  
 <span data-ttu-id="25294-112">指定代理程式是否會嘗試連續處理佇列的交易。</span><span class="sxs-lookup"><span data-stu-id="25294-112">Specifies whether the agent attempts to process queued transactions continuously.</span></span> <span data-ttu-id="25294-113">如果您指定了這個參數，代理程式就會繼續執行，即使所有訂閱者都沒有任何佇列交易暫止也一樣。</span><span class="sxs-lookup"><span data-stu-id="25294-113">If specified, the agent continues execution even if there are no queued transactions pending from any of the subscribers.</span></span>  
  
 <span data-ttu-id="25294-114">**-DefinitionFile** _def_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="25294-114">**-DefinitionFile** _def_path_and_file_name_</span></span>  
 <span data-ttu-id="25294-115">這是代理程式定義檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="25294-115">Is the path of the agent definition file.</span></span> <span data-ttu-id="25294-116">代理程式定義檔包含代理程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="25294-116">An agent definition file contains command-line arguments for the agent.</span></span> <span data-ttu-id="25294-117">此檔案的內容會剖析為可執行檔。</span><span class="sxs-lookup"><span data-stu-id="25294-117">The content of the file is parsed as an executable file.</span></span> <span data-ttu-id="25294-118">請使用雙引號 (") 來指定包含任意字元的引數值。</span><span class="sxs-lookup"><span data-stu-id="25294-118">Use double quotation marks (") to specify argument values containing arbitrary characters.</span></span>  
  
 <span data-ttu-id="25294-119">**-Distributor** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="25294-119">**-Distributor** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="25294-120">這是散發者的名稱。</span><span class="sxs-lookup"><span data-stu-id="25294-120">Is the Distributor name.</span></span> <span data-ttu-id="25294-121">請針對該伺服器上的 *預設執行個體指定* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="25294-121">Specify *server_name* for the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="25294-122">請針對該伺服器上的 *server_name*\\*instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="25294-122">Specify *server_name*\\*instance_name* for a named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="25294-123">如果沒有指定這個參數，此名稱就會預設為本機電腦上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="25294-123">If not specified, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="25294-124">**-DistributionDB** _distribution_database_</span><span class="sxs-lookup"><span data-stu-id="25294-124">**-DistributionDB** _distribution_database_</span></span>  
 <span data-ttu-id="25294-125">這是散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="25294-125">Is the distribution database.</span></span>  
  
 <span data-ttu-id="25294-126">**-DistributorLogin** _distributor_login_</span><span class="sxs-lookup"><span data-stu-id="25294-126">**-DistributorLogin** _distributor_login_</span></span>  
 <span data-ttu-id="25294-127">這是散發者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="25294-127">Is the Distributor login name.</span></span>  
  
 <span data-ttu-id="25294-128">**-DistributorPassword** _distributor_password_</span><span class="sxs-lookup"><span data-stu-id="25294-128">**-DistributorPassword** _distributor_password_</span></span>  
 <span data-ttu-id="25294-129">這是散發者密碼。</span><span class="sxs-lookup"><span data-stu-id="25294-129">Is the Distributor password.</span></span>  
  
 <span data-ttu-id="25294-130">**-DistributorSecurityMode** [ **0**| **1**]</span><span class="sxs-lookup"><span data-stu-id="25294-130">**-DistributorSecurityMode** [ **0**| **1**]</span></span>  
 <span data-ttu-id="25294-131">指定散發者的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="25294-131">Specifies the security mode of the Distributor.</span></span> <span data-ttu-id="25294-132">值為 **0** 表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證模式 (預設值)，而值為 **1** 則表示 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="25294-132">A value of **0** indicates [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication Mode (default), and a value of **1** indicates Windows Authentication Mode.</span></span>  
  
 <span data-ttu-id="25294-133">**-EncryptionLevel** [ **0** | **1** | **2** ]</span><span class="sxs-lookup"><span data-stu-id="25294-133">**-EncryptionLevel** [ **0** | **1** | **2** ]</span></span>  
 <span data-ttu-id="25294-134">這是建立連接時，佇列讀取器代理程式所使用的安全通訊端層 (SSL) 加密層級。</span><span class="sxs-lookup"><span data-stu-id="25294-134">Is the level of Secure Sockets Layer (SSL) encryption used by the Queue Reader Agent when making connections.</span></span>  
  
|<span data-ttu-id="25294-135">EncryptionLevel 值</span><span class="sxs-lookup"><span data-stu-id="25294-135">EncryptionLevel value</span></span>|<span data-ttu-id="25294-136">描述</span><span class="sxs-lookup"><span data-stu-id="25294-136">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="25294-137">**0**</span><span class="sxs-lookup"><span data-stu-id="25294-137">**0**</span></span>|<span data-ttu-id="25294-138">指定不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="25294-138">Specifies that SSL is not used.</span></span>|  
|<span data-ttu-id="25294-139">**1**</span><span class="sxs-lookup"><span data-stu-id="25294-139">**1**</span></span>|<span data-ttu-id="25294-140">指定要使用 SSL，但是代理程式不會驗證 SSL 伺服器憑證是否由受信任的簽發者簽署。</span><span class="sxs-lookup"><span data-stu-id="25294-140">Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.</span></span>|  
|<span data-ttu-id="25294-141">**2**</span><span class="sxs-lookup"><span data-stu-id="25294-141">**2**</span></span>|<span data-ttu-id="25294-142">指定要使用 SSL，而且憑證會經過驗證。</span><span class="sxs-lookup"><span data-stu-id="25294-142">Specifies that SSL is used, and that the certificate is verified.</span></span>|  

 > [!NOTE]  
 >  <span data-ttu-id="25294-143">定義的 SSL 憑證必須包含 SQL Server 的完整網域名稱才會有效。</span><span class="sxs-lookup"><span data-stu-id="25294-143">A valid SSL certificate is defined with a fully qualified domain name of the SQL Server.</span></span> <span data-ttu-id="25294-144">為了讓代理程式能在將 -EncryptionLevel 設定為 2 時成功連線，請在本機 SQL Server 上建立別名。</span><span class="sxs-lookup"><span data-stu-id="25294-144">In order for the agent to connect successfully when setting -EncryptionLevel to 2, create an alias on the local SQL Server.</span></span> <span data-ttu-id="25294-145">'Alias Name' 參數應為伺服器名稱，且應將 'Server' 參數設為 SQL Server 的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="25294-145">The 'Alias Name' parameter should be the server name and the 'Server' parameter should be set to the fully qualified name of the SQL Server.</span></span>
  
 <span data-ttu-id="25294-146">如需詳細資訊，請參閱[SQL Server 複寫安全性](../security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="25294-146">For more information, see [SQL Server Replication Security](../security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="25294-147">**-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="25294-147">**-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="25294-148">指定在佇列讀取器作業期間記錄的記錄量。</span><span class="sxs-lookup"><span data-stu-id="25294-148">Specifies the amount of history logged during a queue reader operation.</span></span> <span data-ttu-id="25294-149">您可以透過選取 **1**，盡量減少記錄作業對效能造成的影響。</span><span class="sxs-lookup"><span data-stu-id="25294-149">You can minimize the effect of history logging on performance by selecting **1**.</span></span>  
  
|<span data-ttu-id="25294-150">HistoryVerboseLevel 值</span><span class="sxs-lookup"><span data-stu-id="25294-150">HistoryVerboseLevel value</span></span>|<span data-ttu-id="25294-151">描述</span><span class="sxs-lookup"><span data-stu-id="25294-151">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="25294-152">**0**</span><span class="sxs-lookup"><span data-stu-id="25294-152">**0**</span></span>|<span data-ttu-id="25294-153">無記錄 (不建議使用)。</span><span class="sxs-lookup"><span data-stu-id="25294-153">No history logging (not recommended).</span></span>|  
|<span data-ttu-id="25294-154">**1**</span><span class="sxs-lookup"><span data-stu-id="25294-154">**1**</span></span>|<span data-ttu-id="25294-155">預設值。</span><span class="sxs-lookup"><span data-stu-id="25294-155">Default.</span></span> <span data-ttu-id="25294-156">一律更新相同狀態的上一個記錄訊息 (啟動、進度、成功等等)。</span><span class="sxs-lookup"><span data-stu-id="25294-156">Always update a previous history message of the same status (startup, progress, success, and so on).</span></span> <span data-ttu-id="25294-157">如果沒有任何具有相同狀態的上一筆記錄存在，便插入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="25294-157">If no previous record with the same status exists, insert a new record.</span></span>|  
|<span data-ttu-id="25294-158">**2**</span><span class="sxs-lookup"><span data-stu-id="25294-158">**2**</span></span>|<span data-ttu-id="25294-159">插入新的記錄，包括閒置訊息或長時間執行作業訊息。</span><span class="sxs-lookup"><span data-stu-id="25294-159">Insert new history records, including idle messages or long-running job messages.</span></span>|  
|<span data-ttu-id="25294-160">**3**</span><span class="sxs-lookup"><span data-stu-id="25294-160">**3**</span></span>|<span data-ttu-id="25294-161">插入新的記錄，包括可用於疑難排解的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="25294-161">Insert new history records that include additional details that may be useful for troubleshooting.</span></span>|  
  
 <span data-ttu-id="25294-162">**-LoginTimeOut** _login_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="25294-162">**-LoginTimeOut** _login_time_out_seconds_</span></span>  
 <span data-ttu-id="25294-163">這是登入逾時之前的秒數。預設為 15 秒。</span><span class="sxs-lookup"><span data-stu-id="25294-163">Is the number of seconds before the login times out. The default is 15 seconds.</span></span>  
  
 <span data-ttu-id="25294-164">**-Output** _output_path_and_file_name_</span><span class="sxs-lookup"><span data-stu-id="25294-164">**-Output** _output_path_and_file_name_</span></span>  
 <span data-ttu-id="25294-165">這是代理程式輸出檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="25294-165">Is the path of the agent output file.</span></span> <span data-ttu-id="25294-166">如果未提供檔案名稱，輸出將傳送至主控台。</span><span class="sxs-lookup"><span data-stu-id="25294-166">If the file name is not provided, the output is sent to the console.</span></span> <span data-ttu-id="25294-167">如果指定的檔案名稱存在，輸出就會附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="25294-167">If the specified file name exists, the output is appended to the file.</span></span>  
  
 <span data-ttu-id="25294-168">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span><span class="sxs-lookup"><span data-stu-id="25294-168">**-OutputVerboseLevel** [ **0**| **1**| **2**]</span></span>  
 <span data-ttu-id="25294-169">指定輸出是否應該詳細。</span><span class="sxs-lookup"><span data-stu-id="25294-169">Specifies whether the output should be verbose.</span></span> <span data-ttu-id="25294-170">如果詳細資訊層級為 0，系統就只會列印錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="25294-170">If the verbose level is **0**, only error messages are printed.</span></span> <span data-ttu-id="25294-171">如果詳細資訊層級為 1，系統就會列印所有進度報表訊息。</span><span class="sxs-lookup"><span data-stu-id="25294-171">If the verbose level is **1**, all the progress report messages are printed.</span></span> <span data-ttu-id="25294-172">如果詳細資訊層級為 2 (預設值)，系統就會列印所有錯誤訊息和進度報表訊息 (可用於偵錯)。</span><span class="sxs-lookup"><span data-stu-id="25294-172">If the verbose level is **2** (default), all error messages and progress report messages are printed, which is useful for debugging.</span></span>  
  
 <span data-ttu-id="25294-173">**-PollingInterval** _polling_interval_</span><span class="sxs-lookup"><span data-stu-id="25294-173">**-PollingInterval** _polling_interval_</span></span>  
 <span data-ttu-id="25294-174">這僅與使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 架構佇列的更新訂閱有關。</span><span class="sxs-lookup"><span data-stu-id="25294-174">Is relevant only for updating subscriptions that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] based queues.</span></span> <span data-ttu-id="25294-175">指定針對暫止佇列交易輪詢 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 佇列的頻率 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="25294-175">Specifies how often, in seconds, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] queue is polled for pending queued transactions.</span></span> <span data-ttu-id="25294-176">此值可介於 0 與 240 秒之間。</span><span class="sxs-lookup"><span data-stu-id="25294-176">The value can be between 0 and 240 seconds.</span></span> <span data-ttu-id="25294-177">預設值是 5 秒。</span><span class="sxs-lookup"><span data-stu-id="25294-177">The default is 5 seconds.</span></span>  
  
 <span data-ttu-id="25294-178">**-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="25294-178">**-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="25294-179">指定參與具有發行集資料庫之資料庫鏡像工作階段的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉夥伴執行個體。</span><span class="sxs-lookup"><span data-stu-id="25294-179">Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] participating in a database mirroring session with the publication database.</span></span> <span data-ttu-id="25294-180">如需詳細資訊，請參閱 [資料庫鏡像和複寫 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="25294-180">For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="25294-181">**-ProfileName** _agent_profile_name_</span><span class="sxs-lookup"><span data-stu-id="25294-181">**-ProfileName** _agent_profile_name_</span></span>  
 <span data-ttu-id="25294-182">這是將一組預設值提供給代理程式所用之代理程式設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="25294-182">Is the name of an agent profile used to supply a set of default values to the agent.</span></span> <span data-ttu-id="25294-183">如需資訊，請參閱[複寫代理程式設定檔](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="25294-183">For information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="25294-184">**-QueryTimeOut** _query_time_out_seconds_</span><span class="sxs-lookup"><span data-stu-id="25294-184">**-QueryTimeOut** _query_time_out_seconds_</span></span>  
 <span data-ttu-id="25294-185">這是查詢逾時之前的秒數。預設值是 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="25294-185">Is the number of seconds before the query times out. The default is 1800 seconds.</span></span>  
  
 <span data-ttu-id="25294-186">**-ResolverState** [ **1**| **2**| **3**]</span><span class="sxs-lookup"><span data-stu-id="25294-186">**-ResolverState** [ **1**| **2**| **3**]</span></span>  
 <span data-ttu-id="25294-187">指定解決佇列更新衝突的方式。</span><span class="sxs-lookup"><span data-stu-id="25294-187">Specifies how queued updating conflicts are resolved.</span></span> <span data-ttu-id="25294-188">值為 **1** 表示發行者在衝突中獲勝，而且目前的衝突佇列交易將在發行者和原始更新訂閱者上回復。後續佇列交易的處理將繼續進行。</span><span class="sxs-lookup"><span data-stu-id="25294-188">A value of **1** indicates the Publisher wins the conflict, and the current conflicting queued transaction will be rolled back on the Publisher and the originating updating Subscriber; the processing of subsequent queued transactions will continue.</span></span> <span data-ttu-id="25294-189">值為 **2** 表示訂閱者在衝突中獲勝，而且佇列交易將覆寫發行者的值。</span><span class="sxs-lookup"><span data-stu-id="25294-189">A value of **2** indicates the Subscriber wins the conflict, and the queued transaction will override the values on the Publisher.</span></span> <span data-ttu-id="25294-190">值為 **3** 表示任何衝突將導致訂閱者重新初始化。發行者在衝突中獲勝、後續佇列交易的處理將結束，而且訂閱將重新初始化。</span><span class="sxs-lookup"><span data-stu-id="25294-190">A value of **3** indicates that any conflict will result in Subscriber re-initialization; the Publisher wins the conflict, processing of subsequent queued transactions will be terminated, and the subscription will be reinitialized.</span></span> <span data-ttu-id="25294-191">交易式發行集的預設設定為 **1** ，而快照式發行集的預設設定為 **3** 。</span><span class="sxs-lookup"><span data-stu-id="25294-191">The default setting is **1** for transactional publications and **3** for snapshot publications.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25294-192">備註</span><span class="sxs-lookup"><span data-stu-id="25294-192">Remarks</span></span>  
 <span data-ttu-id="25294-193">若要啟動佇列讀取器代理程式，請從命令提示字元執行 **qrdrsvc.exe** 。</span><span class="sxs-lookup"><span data-stu-id="25294-193">To start the Queue Reader Agent, execute **qrdrsvc.exe** from the command prompt.</span></span> <span data-ttu-id="25294-194">如需詳細資訊，請參閱＜ [複寫代理程式可執行檔](../concepts/replication-agent-executables-concepts.md)＞。</span><span class="sxs-lookup"><span data-stu-id="25294-194">For information, see [Replication Agent Executables](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25294-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25294-195">See Also</span></span>  
 [<span data-ttu-id="25294-196">複寫代理程式管理</span><span class="sxs-lookup"><span data-stu-id="25294-196">Replication Agent Administration</span></span>](replication-agent-administration.md)  
  
  
