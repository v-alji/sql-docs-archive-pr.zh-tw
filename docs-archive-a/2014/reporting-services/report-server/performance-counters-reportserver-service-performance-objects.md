---
title: ReportServer： Service 和 ReportServerSharePoint： Service 效能物件的效能計數器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Server service, performance counters
ms.assetid: 2bcacab2-3a4f-4aae-b123-19d756b9b9ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8244f22797ac284d7037bad445f12e0f9c117d55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700801"
---
# <a name="performance-counters-for-the-reportserverservice--and-reportserversharepointservice-performance-objects"></a><span data-ttu-id="0f950-102">ReportServer:Service 和 ReportServerSharePoint:Service 效能物件的效能計數器</span><span class="sxs-lookup"><span data-stu-id="0f950-102">Performance Counters for the ReportServer:Service  and ReportServerSharePoint:Service Performance Objects</span></span>
  <span data-ttu-id="0f950-103">本主題描述下列 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 效能物件的效能計數器：</span><span class="sxs-lookup"><span data-stu-id="0f950-103">This topic describes performance counters for the following [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] performance objects:</span></span>

-   `ReportServer:Service`

-   `ReportServerSharePoint:Service`

> [!NOTE]
>  <span data-ttu-id="0f950-104">效能物件是用來監視本機報表伺服器的事件。</span><span class="sxs-lookup"><span data-stu-id="0f950-104">The performance objects are used to monitor events on the local report server.</span></span> <span data-ttu-id="0f950-105">如果您是在向外延展部署中執行報表伺服器，則計數會套用到目前的伺服器，而非整個向外延展部署。</span><span class="sxs-lookup"><span data-stu-id="0f950-105">If you are running a report server in a scale-out deployment, the counts apply to the current server and not the scale-out deployment as a whole.</span></span>

 <span data-ttu-id="0f950-106">Windows 效能監視器 (**Perfmon.exe**) 中提供了效能物件。</span><span class="sxs-lookup"><span data-stu-id="0f950-106">The performance objects are available in the Windows Performance Monitor (**Perfmon.exe**).</span></span> <span data-ttu-id="0f950-107">如需詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="0f950-107">For more information, see the Windows documentation.</span></span> <span data-ttu-id="0f950-108">[執行階段分析](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="0f950-108">[Runtime Profiling](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx).</span></span>

 <span data-ttu-id="0f950-109">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="0f950-109">In this topic:</span></span>

-   [<span data-ttu-id="0f950-110">ReportServer:Service 效能計數器 (原生模式報表伺服器)</span><span class="sxs-lookup"><span data-stu-id="0f950-110">ReportServer:Service Performance Counters (Native Mode Report Server)</span></span>](#bkmk_ReportServer)

-   [<span data-ttu-id="0f950-111">ReportServerSharePoint:Service (SharePoint 模式報表伺服器)</span><span class="sxs-lookup"><span data-stu-id="0f950-111">ReportServerSharePoint:Service (SharePoint Mode Report Server)</span></span>](#bkmk_ReportServerSharePoint)

-   [<span data-ttu-id="0f950-112">使用 PowerShell 指令程式傳回清單</span><span class="sxs-lookup"><span data-stu-id="0f950-112">Use PowerShell Cmdlets to return lists</span></span>](#bkmk_powershell)

 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="0f950-113">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]SharePoint 模式 |原生模式。</span><span class="sxs-lookup"><span data-stu-id="0f950-113">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode | Native mode.</span></span>

##  <a name="reportserverservice-performance-counters-native-mode-report-server"></a><a name="bkmk_ReportServer"></a> <span data-ttu-id="0f950-114">ReportServer:Service 效能計數器 (原生模式報表伺服器)</span><span class="sxs-lookup"><span data-stu-id="0f950-114">ReportServer:Service Performance Counters (Native Mode Report Server)</span></span>
 <span data-ttu-id="0f950-115">`ReportServer:Service` 效能物件包含一組計數器集合，用來追蹤報表伺服器執行個體的 HTTP 相關事件和記憶體相關事件。</span><span class="sxs-lookup"><span data-stu-id="0f950-115">The `ReportServer:Service` performance object includes a collection of counters to track HTTP-related events and memory-related events for a report server instance.</span></span> <span data-ttu-id="0f950-116">這個效能物件會針對電腦上的每個 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 執行個體顯示一次，而且您可以在每個執行個體的效能物件中加入或移除計數器。</span><span class="sxs-lookup"><span data-stu-id="0f950-116">This performance object appears one time for each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] instance on the computer, and you can add or remove counters from the performance object for each instance.</span></span> <span data-ttu-id="0f950-117">預設執行個體的計數器會以 `ReportServer:Service` 格式顯示。</span><span class="sxs-lookup"><span data-stu-id="0f950-117">Counters for the default instance appear in the format `ReportServer:Service`.</span></span> <span data-ttu-id="0f950-118">命名實例的計數器會以 instance_name 的格式顯示 `ReportServer$<` *instance_name* `>:Service` 。</span><span class="sxs-lookup"><span data-stu-id="0f950-118">Counters for named instances appear in the format `ReportServer$<`*instance_name*`>:Service`.</span></span>

 <span data-ttu-id="0f950-119">`ReportServer:Service`效能物件是的新功能 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ，它提供了 Internet Information Services (IIS) 和舊版中所包含的計數器子集 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0f950-119">The `ReportServer:Service` performance object was new in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], and it provides a subset of counters that were included with Internet Information Services (IIS) and [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] in previous versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="0f950-120">這些新的計數器是 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]特有的，而且它們會追蹤報表伺服器的 HTTP 相關事件，例如要求、連接和登入嘗試。</span><span class="sxs-lookup"><span data-stu-id="0f950-120">These new counters are specific to [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], and they track HTTP-related events for the report server, such as requests, connections, and logon attempts.</span></span> <span data-ttu-id="0f950-121">此外，這個效能物件包含可追蹤記憶體管理事件的計數器。</span><span class="sxs-lookup"><span data-stu-id="0f950-121">Additionally, this performance object includes counters to track memory management events.</span></span>

 <span data-ttu-id="0f950-122">下表將列出 `ReportServer:Service` 效能物件所包含的計數器。</span><span class="sxs-lookup"><span data-stu-id="0f950-122">The following table lists the counters that are included in the `ReportServer:Service` performance object.</span></span>

 <span data-ttu-id="0f950-123">![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容") 下列 Windows PowerShell 指令碼將會傳回 CounterSetName 的效能計數器清單</span><span class="sxs-lookup"><span data-stu-id="0f950-123">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content") The following Windows PowerShell script will return the list of performance counters for the CounterSetName</span></span>

```
(get-counter -listset "ReportServer:Service").paths
```

|<span data-ttu-id="0f950-124">計數器</span><span class="sxs-lookup"><span data-stu-id="0f950-124">Counter</span></span>|<span data-ttu-id="0f950-125">描述</span><span class="sxs-lookup"><span data-stu-id="0f950-125">Description</span></span>|
|-------------|-----------------|
|`Active connections`|<span data-ttu-id="0f950-126">目前在伺服器上作用中的連接數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-126">The number of connections currently active on the server.</span></span>|
|`Bytes Received Total`|<span data-ttu-id="0f950-127">伺服器所接收的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-127">The number of bytes received by the server.</span></span> <span data-ttu-id="0f950-128">這個計數器會計算報表管理員和報表伺服器所接收的原始位元組總計。</span><span class="sxs-lookup"><span data-stu-id="0f950-128">This counter counts the raw bytes received in total by both Report Manager and the report server.</span></span>|
|`Bytes Received/sec`|<span data-ttu-id="0f950-129">伺服器每秒所接收的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-129">The number of bytes received per second by the server.</span></span> <span data-ttu-id="0f950-130">只有當傳送完成時，才會更新這個計數器。</span><span class="sxs-lookup"><span data-stu-id="0f950-130">This counter is updated only when a transfer is completed.</span></span> <span data-ttu-id="0f950-131">這表示此計數器會維持 0，然後此值在傳送完成之後才會增加。</span><span class="sxs-lookup"><span data-stu-id="0f950-131">This means that the counter remains at 0 and then the value increases after a transfer is complete.</span></span>|
|`Bytes Sent Total`|<span data-ttu-id="0f950-132">伺服器所傳送的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-132">The number of bytes sent from the server.</span></span> <span data-ttu-id="0f950-133">這個計數器會計算報表管理員和報表伺服器所傳送的原始位元組總計。</span><span class="sxs-lookup"><span data-stu-id="0f950-133">This counter counts the raw bytes sent in total by both Report Manager and the report server.</span></span>|
|`Bytes Sent/sec`|<span data-ttu-id="0f950-134">伺服器每秒所傳送的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-134">The number of bytes sent per second from the server.</span></span> <span data-ttu-id="0f950-135">只有當傳送完成時，才會更新這個計數器。</span><span class="sxs-lookup"><span data-stu-id="0f950-135">This counter is updated only when a transfer is completed.</span></span> <span data-ttu-id="0f950-136">這表示此計數器會維持 0，然後此值在傳送完成之後才會增加。</span><span class="sxs-lookup"><span data-stu-id="0f950-136">This means that the counter remains at 0 and then the value increases after a transfer is complete.</span></span>|
|`Errors Total`|<span data-ttu-id="0f950-137">在處理 HTTP 要求期間發生的錯誤總數。</span><span class="sxs-lookup"><span data-stu-id="0f950-137">The total number of errors that occur during the processing of HTTP requests.</span></span> <span data-ttu-id="0f950-138">這些錯誤包括 400s 和 500s 中的 HTTP 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="0f950-138">These errors include HTTP status codes in the 400s and 500s.</span></span>|
|`Errors/sec`|<span data-ttu-id="0f950-139">在處理 HTTP 要求期間每秒發生的錯誤總數。</span><span class="sxs-lookup"><span data-stu-id="0f950-139">The total number of errors that occur per second during the processing of HTTP requests.</span></span> <span data-ttu-id="0f950-140">這些錯誤包括 400s 和 500s 中的 HTTP 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="0f950-140">These errors include HTTP status codes in the 400s and 500s.</span></span>|
|`Logon Attempts Total`|<span data-ttu-id="0f950-141">RSWindows 驗證類型已經嘗試登入的次數。</span><span class="sxs-lookup"><span data-stu-id="0f950-141">The number of logon attempts made from RSWindows authentication types.</span></span> <span data-ttu-id="0f950-142">RSWindows 驗證類型包括 RSWindowsNegotiate、RSWindowsNTLM、RSWindowsKerberos 和 RSWindowsBasic。</span><span class="sxs-lookup"><span data-stu-id="0f950-142">RSWindows authentication types include RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos, and RSWindowsB asic.</span></span> <span data-ttu-id="0f950-143">值為零 (0) 表示自訂驗證。</span><span class="sxs-lookup"><span data-stu-id="0f950-143">The value zero (0) represents Custom authentication.</span></span>|
|`Logon Attempts/sec`|<span data-ttu-id="0f950-144">嘗試登入的速率。</span><span class="sxs-lookup"><span data-stu-id="0f950-144">The rate of logon attempts.</span></span>|
|`Logon Successes Total`|<span data-ttu-id="0f950-145">RSWindows 驗證類型成功登入的次數。</span><span class="sxs-lookup"><span data-stu-id="0f950-145">The number of successful logons for RSWindows authentication types.</span></span> <span data-ttu-id="0f950-146">RSWindows 驗證類型包括 RSWindowsNegotiate、RSWindowsNTLM、RSWindowsKerberos 和 RSWindowsBasic。</span><span class="sxs-lookup"><span data-stu-id="0f950-146">RSWindows authentication types include RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos, and RSWindowsB asic.</span></span> <span data-ttu-id="0f950-147">值為零 (0) 表示自訂驗證。</span><span class="sxs-lookup"><span data-stu-id="0f950-147">The value zero (0) represents Custom authentication.</span></span>|
|`Logon Successes/sec`|<span data-ttu-id="0f950-148">成功登入的速率。</span><span class="sxs-lookup"><span data-stu-id="0f950-148">The rate of successful logons.</span></span>|
|`Memory Pressure State`|<span data-ttu-id="0f950-149">下列其中一個數字 (從 1 到 5)，表示伺服器目前的記憶體狀態：</span><span class="sxs-lookup"><span data-stu-id="0f950-149">One of the following numbers, from 1-5, which indicates the current memory state of the server:</span></span><br /><br /> <span data-ttu-id="0f950-150">1：沒有壓力</span><span class="sxs-lookup"><span data-stu-id="0f950-150">1: No pressure</span></span><br /><br /> <span data-ttu-id="0f950-151">2：低度壓力</span><span class="sxs-lookup"><span data-stu-id="0f950-151">2: Low pressure</span></span><br /><br /> <span data-ttu-id="0f950-152">3：中度壓力</span><span class="sxs-lookup"><span data-stu-id="0f950-152">3: Medium pressure</span></span><br /><br /> <span data-ttu-id="0f950-153">4：高度壓力</span><span class="sxs-lookup"><span data-stu-id="0f950-153">4: High pressure</span></span><br /><br /> <span data-ttu-id="0f950-154">5：壓力過高</span><span class="sxs-lookup"><span data-stu-id="0f950-154">5: Exceeded pressure</span></span>|
|`Memory Shrink Amount`|<span data-ttu-id="0f950-155">伺服器要求壓縮使用中記憶體的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-155">The number of bytes that the server requested to shrink the memory in use.</span></span>|
|`Memory Shrink Notifications/sec`|<span data-ttu-id="0f950-156">伺服器在上一秒發出以壓縮使用中記憶體的通知數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-156">The number of notifications that the server issued in the last second to shrink the memory in use.</span></span> <span data-ttu-id="0f950-157">這個值表示伺服器遇到記憶體壓力的頻率。</span><span class="sxs-lookup"><span data-stu-id="0f950-157">This value indicates how often the server experiences memory pressure.</span></span>|
|`Requests Disconnected`|<span data-ttu-id="0f950-158">由於通訊失敗而造成中斷連接的要求數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-158">The number of requests that are disconnected because of a communication failure.</span></span>|
|`Requests Executing`|<span data-ttu-id="0f950-159">目前正在處理的要求數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-159">The number of requests that are currently processing.</span></span>|
|`Requests Not Authorized`|<span data-ttu-id="0f950-160">失敗而且出現 HTTP 401 狀態碼的要求數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-160">The number of requests that fail with an HTTP 401 status code.</span></span>|
|`Requests Rejected`|<span data-ttu-id="0f950-161">由於伺服器資源不足而未處理的要求總數。</span><span class="sxs-lookup"><span data-stu-id="0f950-161">The total number of requests that were not processed because of insufficient server resources.</span></span> <span data-ttu-id="0f950-162">這個計數器表示傳回 HTTP 503 狀態碼 (表示伺服器太過忙碌) 的要求數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-162">This counter represents the number of requests that return a HTTP 503 status code, which indicates that the server is too busy.</span></span>|
|`Requests Total`|<span data-ttu-id="0f950-163">報表伺服器服務啟動以來所收到的要求總數。</span><span class="sxs-lookup"><span data-stu-id="0f950-163">The total number of requests that are received by the report server service since startup.</span></span> <span data-ttu-id="0f950-164">這個計數器會計算傳送至報表管理員的要求，以及從報表管理員傳送至報表伺服器的要求。</span><span class="sxs-lookup"><span data-stu-id="0f950-164">This counter counts requests that are sent to Report Manager and requests that are sent from Report Manager to the report server.</span></span>|
|`Requests/sec`|<span data-ttu-id="0f950-165">每秒處理的要求數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-165">The number of requests that are processed per second.</span></span> <span data-ttu-id="0f950-166">這個值代表應用程式目前的輸送量。</span><span class="sxs-lookup"><span data-stu-id="0f950-166">This value represents the current throughput of the application.</span></span>|
|`Tasks Queued`|<span data-ttu-id="0f950-167">等候執行緒成為可用於處理的工作數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-167">The number of tasks that are waiting for a thread to become available for processing.</span></span> <span data-ttu-id="0f950-168">對報表伺服器提出的每一要求會對應到一個或多個工作。</span><span class="sxs-lookup"><span data-stu-id="0f950-168">Each request made to the report server corresponds to one or more tasks.</span></span> <span data-ttu-id="0f950-169">這個計數器只表示準備進行處理的工作數目，並不包括目前執行中的工作數目。</span><span class="sxs-lookup"><span data-stu-id="0f950-169">This counter represents only the number of tasks that are ready for processing; it does not include the number of tasks that are currently running.</span></span>|

##  <a name="reportserversharepointservice-sharepoint-mode-report-server"></a><a name="bkmk_ReportServerSharePoint"></a> <span data-ttu-id="0f950-170">ReportServerSharePoint:Service (SharePoint 模式報表伺服器)</span><span class="sxs-lookup"><span data-stu-id="0f950-170">ReportServerSharePoint:Service (SharePoint Mode Report Server)</span></span>
 <span data-ttu-id="0f950-171">`ReportServerSharePoint:Service`效能物件已加入中 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0f950-171">The `ReportServerSharePoint:Service` performance object was added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

 <span data-ttu-id="0f950-172">![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容") 下列 Windows PowerShell 指令碼將會傳回 CounterSetName 的效能計數器清單</span><span class="sxs-lookup"><span data-stu-id="0f950-172">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content") The following Windows PowerShell script will return the list of performance counters for the CounterSetName</span></span>

```
(get-counter -listset "ReportServerSharePoint:Service").paths
```

|<span data-ttu-id="0f950-173">計數器</span><span class="sxs-lookup"><span data-stu-id="0f950-173">Counter</span></span>|
|-------------|
|`Memory Pressure State`|
|`Memory Shrink Amount`|
|`Memory Shrink Notifications/Sec`|

##  <a name="use-powershell-cmdlets-to-return-lists"></a><a name="bkmk_powershell"></a><span data-ttu-id="0f950-174">使用 PowerShell Cmdlet 來傳回清單</span><span class="sxs-lookup"><span data-stu-id="0f950-174">Use PowerShell Cmdlets to return lists</span></span>
 <span data-ttu-id="0f950-175">![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容") 下列 Windows PowerShell 指令碼將會傳回 CounterSetName "ReportServerSharePoint:Service" 的效能計數器清單：</span><span class="sxs-lookup"><span data-stu-id="0f950-175">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content") The following Windows PowerShell script will return the list of performance counters for the CounterSetName "ReportServerSharePoint:Service":</span></span>

```
(get-counter -listset "ReportServerSharePoint:Service").paths
```

## <a name="see-also"></a><span data-ttu-id="0f950-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f950-176">See Also</span></span>
 <span data-ttu-id="0f950-177">[監視](monitoring-report-server-performance.md) [MSRS 2014 WEB 服務和 MSRS 2014 Windows 服務效能物件的報表伺服器效能效能計數器 &#40;原生模式&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md) [MSRS 2014 Web 服務 Sharepoint 模式的效能計數器] 和 [MSRS 2014 Windows 服務 Sharepoint 模式] 效能物件 &#40;sharepoint 模式&#41;]。/performance-counters-msrs-2011-sharepoint-mode-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="0f950-177">[Monitoring Report Server Performance](monitoring-report-server-performance.md) [Performance Counters for the MSRS 2014 Web Service and MSRS 2014 Windows Service Performance Objects &#40;Native Mode&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md) [Performance Counters for the MSRS 2014 Web Service SharePoint Mode and MSRS 2014 Windows Service SharePoint Mode Performance Objects &#40;SharePoint Mode&#41;]../performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)</span></span>


