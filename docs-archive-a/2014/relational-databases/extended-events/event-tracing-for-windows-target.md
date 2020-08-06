---
title: Windows 事件追蹤目標 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- event tracing for windows target
- ETW target
- targets [SQL Server extended events], event tracing for windows target
ms.assetid: ca2bb295-b7f6-49c3-91ed-0ad4c39f89d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 55f247af30b5278f614b6505a94266cc07ec6c54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592024"
---
# <a name="event-tracing-for-windows-target"></a><span data-ttu-id="fd02e-102">Windows 事件追蹤目標</span><span class="sxs-lookup"><span data-stu-id="fd02e-102">Event Tracing for Windows Target</span></span>
  <span data-ttu-id="fd02e-103">使用 Windows 事件追蹤 (ETW) 當做目標之前，我們建議您最好具備 ETW 的實用知識。</span><span class="sxs-lookup"><span data-stu-id="fd02e-103">Before you use Event Tracing for Windows (ETW) as a target, we recommend that you have a working knowledge of ETW.</span></span> <span data-ttu-id="fd02e-104">ETW 追蹤會搭配擴充事件一起使用，或是當做擴充事件的事件取用者使用。</span><span class="sxs-lookup"><span data-stu-id="fd02e-104">ETW tracing is either used together with Extended Events or as an Extended Events event consumer.</span></span> <span data-ttu-id="fd02e-105">下列外部連結提供取得有關 ETW 之背景資訊的起點：</span><span class="sxs-lookup"><span data-stu-id="fd02e-105">The following external links provide a starting point for obtaining background information about ETW:</span></span>  
  
-   [<span data-ttu-id="fd02e-106">Windows 事件</span><span class="sxs-lookup"><span data-stu-id="fd02e-106">Windows Events</span></span>](https://go.microsoft.com/fwlink/?LinkId=92380)  
  
-   [<span data-ttu-id="fd02e-107">使用 ETW 改善偵錯和效能調整</span><span class="sxs-lookup"><span data-stu-id="fd02e-107">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=92381)  
  
 <span data-ttu-id="fd02e-108">ETW 目標是單一目標，但是此目標可加入至許多工作階段。</span><span class="sxs-lookup"><span data-stu-id="fd02e-108">The ETW target is a singleton target, although the target can be added to many sessions.</span></span> <span data-ttu-id="fd02e-109">如果某個事件在許多工作階段上引發，只會在每次發生事件時，將該事件傳播至 ETW 目標一次。</span><span class="sxs-lookup"><span data-stu-id="fd02e-109">If an event is raised on many sessions, the event will only be propagated to the ETW target one time per event occurrence.</span></span> <span data-ttu-id="fd02e-110">在每一個處理序上，擴充事件引擎則限制為單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="fd02e-110">The Extended Events engine is limited to a single instance per process.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fd02e-111">為了讓 ETW 目標運作， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務啟動帳戶必須是 Performance Log Users 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="fd02e-111">For the ETW target to work, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service startup account must be a member of the Performance Log Users group.</span></span>  
  
 <span data-ttu-id="fd02e-112">ETW 工作階段中的事件組態是由裝載擴充事件引擎的處理序所控制。</span><span class="sxs-lookup"><span data-stu-id="fd02e-112">The configuration of the events present in an ETW session is controlled by the process that hosts the Extended Events engine.</span></span> <span data-ttu-id="fd02e-113">此引擎會控制要引發的事件以及讓事件發生所必須符合的條件。</span><span class="sxs-lookup"><span data-stu-id="fd02e-113">The engine controls which events to raise and what conditions must be met for an event to occur.</span></span>  
  
 <span data-ttu-id="fd02e-114">當繫結至擴充事件工作階段之後 (在處理序存留期間第一次附加 ETW 目標)，ETW 目標會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供者上開啟單一 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="fd02e-114">After binding to an Extended Events session, which attaches the ETW target for the first time during the lifetime of a process, the ETW target opens a single ETW session on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider.</span></span> <span data-ttu-id="fd02e-115">如果 ETW 工作階段已經存在，ETW 目標會取得現有工作階段的參考。</span><span class="sxs-lookup"><span data-stu-id="fd02e-115">If an ETW session already exists, the ETW target obtains a reference to the existing session.</span></span> <span data-ttu-id="fd02e-116">這個 ETW 工作階段可在給定電腦上的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間共用，</span><span class="sxs-lookup"><span data-stu-id="fd02e-116">This ETW session is shared across all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on a given computer.</span></span> <span data-ttu-id="fd02e-117">這個 ETW 工作階段會從具有 ETW 目標的工作階段中接收所有事件。</span><span class="sxs-lookup"><span data-stu-id="fd02e-117">This ETW session receives all the events from sessions that have the ETW target.</span></span>  
  
 <span data-ttu-id="fd02e-118">因為 ETW 需要啟用提供者，才能取用事件並將事件往下流向 ETW，所以會在此工作階段上啟用所有擴充的事件封裝。</span><span class="sxs-lookup"><span data-stu-id="fd02e-118">Because ETW needs providers to be enabled to consume events and flow them down to the ETW, all Extended Events packages are enabled on the session.</span></span> <span data-ttu-id="fd02e-119">當引發事件時，ETW 目標會傳送此事件到工作階段 (此工作階段上已啟用此事件的提供者)。</span><span class="sxs-lookup"><span data-stu-id="fd02e-119">When an event is fired, the ETW target sends the event to the session on which the provider for the event is enabled.</span></span>  
  
 <span data-ttu-id="fd02e-120">ETW 目標支援在引發事件的執行緒上同步發行事件。</span><span class="sxs-lookup"><span data-stu-id="fd02e-120">The ETW target supports synchronous publishing of events on the thread that raises the event.</span></span> <span data-ttu-id="fd02e-121">不過，ETW 目標不支援非同步的事件發行。</span><span class="sxs-lookup"><span data-stu-id="fd02e-121">However, the ETW target does not support asynchronous event publishing.</span></span>  
  
 <span data-ttu-id="fd02e-122">ETW 目標不支援來自外部 ETW 控制器的控制，例如 Logman.exe。</span><span class="sxs-lookup"><span data-stu-id="fd02e-122">The ETW target does not support control from external ETW controllers such as Logman.exe.</span></span> <span data-ttu-id="fd02e-123">若要產生 ETW 追蹤，您必須使用 ETW 目標來建立事件工作階段。</span><span class="sxs-lookup"><span data-stu-id="fd02e-123">To produce ETW traces, an event session must be created with the ETW target.</span></span> <span data-ttu-id="fd02e-124">如需詳細資訊，請參閱 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fd02e-124">For more information, see [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd02e-125">啟用 ETW 目標就會建立名為 XE_DEFAULT_ETW_SESSION 的 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="fd02e-125">Enabling the ETW target creates an ETW session that is named XE_DEFAULT_ETW_SESSION.</span></span> <span data-ttu-id="fd02e-126">如果具有 XE_DEFAULT_ETW_SESSION 名稱的工作階段已經存在，就會使用此工作階段，而不修改現有工作階段的任何屬性。</span><span class="sxs-lookup"><span data-stu-id="fd02e-126">If a session with the name XE_DEFAULT_ETW_SESSION already exists, it is used without modifying any properties of the existing session.</span></span> <span data-ttu-id="fd02e-127">XE_DEFAULT_ETW_SESSION 會在所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體之間共用。</span><span class="sxs-lookup"><span data-stu-id="fd02e-127">The XE_DEFAULT_ETW_SESSION is shared between all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fd02e-128">啟動 XE_DEFAULT_ETW_SESSION 之後，您必須使用 Logman 工具等 ETW 控制器來停止它。</span><span class="sxs-lookup"><span data-stu-id="fd02e-128">After you start the XE_DEFAULT_ETW_SESSION, you must stop it by using an ETW controller, such as the Logman tool.</span></span> <span data-ttu-id="fd02e-129">例如，你可以在命令提示字元中執行下列命令：`logman stop XE_DEFAULT_ETW_SESSION -ets`。</span><span class="sxs-lookup"><span data-stu-id="fd02e-129">For example, you can run the following command at the command prompt: `logman stop XE_DEFAULT_ETW_SESSION -ets`.</span></span>  
  
 <span data-ttu-id="fd02e-130">下表描述用於設定 ETW 目標的可用選項。</span><span class="sxs-lookup"><span data-stu-id="fd02e-130">The following table describes the available options for configuring the ETW target.</span></span>  
  
|<span data-ttu-id="fd02e-131">選項</span><span class="sxs-lookup"><span data-stu-id="fd02e-131">Option</span></span>|<span data-ttu-id="fd02e-132">允許的值</span><span class="sxs-lookup"><span data-stu-id="fd02e-132">Allowed values</span></span>|<span data-ttu-id="fd02e-133">描述</span><span class="sxs-lookup"><span data-stu-id="fd02e-133">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="fd02e-134">default_xe_session_name</span><span class="sxs-lookup"><span data-stu-id="fd02e-134">default_xe_session_name</span></span>|<span data-ttu-id="fd02e-135">最多 256 個字元的任何字串。</span><span class="sxs-lookup"><span data-stu-id="fd02e-135">Any string up to 256 characters.</span></span> <span data-ttu-id="fd02e-136">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="fd02e-136">This value is optional.</span></span>|<span data-ttu-id="fd02e-137">擴充事件工作階段名稱。</span><span class="sxs-lookup"><span data-stu-id="fd02e-137">The Extended Events session name.</span></span> <span data-ttu-id="fd02e-138">根據預設，這個名稱是 XE_DEFAULT_ETW_SESSION。</span><span class="sxs-lookup"><span data-stu-id="fd02e-138">By default, this is XE_DEFAULT_ETW_SESSION.</span></span>|  
|<span data-ttu-id="fd02e-139">default_etw_session_logfile_path</span><span class="sxs-lookup"><span data-stu-id="fd02e-139">default_etw_session_logfile_path</span></span>|<span data-ttu-id="fd02e-140">最多 256 個字元的任何字串。</span><span class="sxs-lookup"><span data-stu-id="fd02e-140">Any string up to 256 characters.</span></span> <span data-ttu-id="fd02e-141">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="fd02e-141">This value is optional.</span></span>|<span data-ttu-id="fd02e-142">擴充事件工作階段之記錄檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="fd02e-142">The path of the log file for the Extended Events session.</span></span> <span data-ttu-id="fd02e-143">根據預設，這個路徑是 %TEMP%\ XEEtw.etl。</span><span class="sxs-lookup"><span data-stu-id="fd02e-143">By default, this is %TEMP%\ XEEtw.etl.</span></span>|  
|<span data-ttu-id="fd02e-144">default_etw_session_logfile_size_mb</span><span class="sxs-lookup"><span data-stu-id="fd02e-144">default_etw_session_logfile_size_mb</span></span>|<span data-ttu-id="fd02e-145">任何不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="fd02e-145">Any unsigned integer.</span></span> <span data-ttu-id="fd02e-146">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="fd02e-146">This value is optional.</span></span>|<span data-ttu-id="fd02e-147">擴充事件工作階段的記錄檔案大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="fd02e-147">The log file size, in megabytes (MB), for the Extended Events session.</span></span> <span data-ttu-id="fd02e-148">預設值是 20 MB。</span><span class="sxs-lookup"><span data-stu-id="fd02e-148">The default is 20 MB.</span></span>|  
|<span data-ttu-id="fd02e-149">default_etw_session_buffer_size_kb</span><span class="sxs-lookup"><span data-stu-id="fd02e-149">default_etw_session_buffer_size_kb</span></span>|<span data-ttu-id="fd02e-150">任何不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="fd02e-150">Any unsigned integer.</span></span> <span data-ttu-id="fd02e-151">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="fd02e-151">This value is optional.</span></span>|<span data-ttu-id="fd02e-152">擴充事件工作階段的記憶體中緩衝區大小 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="fd02e-152">The in-memory buffer size, in kilobytes (KB), for the Extended Events session.</span></span> <span data-ttu-id="fd02e-153">預設值是 128 KB。</span><span class="sxs-lookup"><span data-stu-id="fd02e-153">The default is 128 KB.</span></span>|  
|<span data-ttu-id="fd02e-154">重試</span><span class="sxs-lookup"><span data-stu-id="fd02e-154">retries</span></span>|<span data-ttu-id="fd02e-155">任何不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="fd02e-155">Any unsigned integer.</span></span>|<span data-ttu-id="fd02e-156">在卸除事件之前，重試將此事件發行給 ETW 子系統的次數。</span><span class="sxs-lookup"><span data-stu-id="fd02e-156">The number of times to retry publishing the event to the ETW subsystem before dropping the event.</span></span> <span data-ttu-id="fd02e-157">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="fd02e-157">The default is 0.</span></span>|  
  
 <span data-ttu-id="fd02e-158">這些設定都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="fd02e-158">Configuring these settings is optional.</span></span> <span data-ttu-id="fd02e-159">ETW 目標會使用這些設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="fd02e-159">The ETW target uses default values for these settings.</span></span>  
  
 <span data-ttu-id="fd02e-160">ETW 目標負責以下工作：</span><span class="sxs-lookup"><span data-stu-id="fd02e-160">The ETW target is responsible for:</span></span>  
  
-   <span data-ttu-id="fd02e-161">建立預設 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="fd02e-161">Creating the default ETW session.</span></span>  
  
-   <span data-ttu-id="fd02e-162">將所有擴充的事件封裝向 ETW 註冊。</span><span class="sxs-lookup"><span data-stu-id="fd02e-162">Registering all Extended Events packages with ETW.</span></span> <span data-ttu-id="fd02e-163">如此可確保 ETW 不會卸除事件。</span><span class="sxs-lookup"><span data-stu-id="fd02e-163">This ensures that events are not dropped by ETW.</span></span>  
  
-   <span data-ttu-id="fd02e-164">管理對 ETW 的事件流程。</span><span class="sxs-lookup"><span data-stu-id="fd02e-164">Managing the flow of events to ETW.</span></span> <span data-ttu-id="fd02e-165">ETW 目標會以擴充的事件資料來建立 ETW 事件，然後將它傳送給適當的 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="fd02e-165">The ETW target creates an ETW event with Extended Events data and sends it to the appropriate ETW session.</span></span> <span data-ttu-id="fd02e-166">如果此事件大於緩衝區大小，或是資料無法納入一個 ETW 事件中，則 ETW 會將此事件分割若干片段。</span><span class="sxs-lookup"><span data-stu-id="fd02e-166">If the event is larger than the buffer size, or data cannot fit in one ETW event, ETW splits the event into fragments.</span></span>  
  
-   <span data-ttu-id="fd02e-167">請隨時將擴充的事件封裝保持在啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="fd02e-167">Keeping Extended Events packages enabled at all times.</span></span>  
  
 <span data-ttu-id="fd02e-168">下列的預設檔案位置是由 ETW 所使用：</span><span class="sxs-lookup"><span data-stu-id="fd02e-168">The following default file locations are used by ETW:</span></span>  
  
-   <span data-ttu-id="fd02e-169">ETW 輸出檔位於 %TEMP%\XEEtw.etl 中。</span><span class="sxs-lookup"><span data-stu-id="fd02e-169">The ETW output file is in %TEMP%\XEEtw.etl.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fd02e-170">當第一個工作階段啟動之後，將無法變更檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="fd02e-170">The file path cannot be changed after the first session starts.</span></span>  
  
-   <span data-ttu-id="fd02e-171">受控物件格式 (MOF) 檔案位於 *\<your install path>* \Microsoft SQL Server\Shared 中。</span><span class="sxs-lookup"><span data-stu-id="fd02e-171">Managed Object Format (MOF) files are in *\<your install path>* \Microsoft SQL Server\Shared.</span></span> <span data-ttu-id="fd02e-172">如需詳細資訊，請參閱 MSDN 上的 [Managed Object Format (MOF)](https://go.microsoft.com/fwlink/?LinkId=92851) (管理物件格式)。</span><span class="sxs-lookup"><span data-stu-id="fd02e-172">For more information, see [Managed Object Format](https://go.microsoft.com/fwlink/?LinkId=92851) on MSDN.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="fd02e-173">將目標加入至工作階段</span><span class="sxs-lookup"><span data-stu-id="fd02e-173">Adding the Target to a Session</span></span>  
 <span data-ttu-id="fd02e-174">若要將 ETW 目標加入至擴充事件工作階段，您必須在建立或改變事件工作階段時，加入下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="fd02e-174">To add the ETW target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.etw_classic_sync_target  
```  
  
 <span data-ttu-id="fd02e-175">如需示範如何使用 ETW 目標 (包括如何檢視資料) 之完整範例的詳細資訊，請參閱 [使用擴充事件監視系統活動](monitor-system-activity-using-extended-events.md)。</span><span class="sxs-lookup"><span data-stu-id="fd02e-175">For more information about a full example that shows how to use the ETW target, including how to view the data, see [Monitor System Activity Using Extended Events](monitor-system-activity-using-extended-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd02e-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd02e-176">See Also</span></span>  
 <span data-ttu-id="fd02e-177">[SQL Server 擴充的事件目標](../../database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="fd02e-177">[SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="fd02e-178">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fd02e-178">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="fd02e-179">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fd02e-179">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="fd02e-180">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd02e-180">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
