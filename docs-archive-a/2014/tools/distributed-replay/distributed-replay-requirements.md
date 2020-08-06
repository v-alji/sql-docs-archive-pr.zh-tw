---
title: Distributed Replay 需求 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 6fffee7d-891f-4d9d-b2c3-dd19855a1c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 66be93534756360e722fcccaf405815e14ffa7ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595326"
---
# <a name="distributed-replay-requirements"></a><span data-ttu-id="74456-102">Distributed Replay Requirements</span><span class="sxs-lookup"><span data-stu-id="74456-102">Distributed Replay Requirements</span></span>
  <span data-ttu-id="74456-103">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 功能之前，請先考慮本主題所列的各項產品需求。</span><span class="sxs-lookup"><span data-stu-id="74456-103">Before using the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay feature, consider the product requirements that are outlined in this topic.</span></span>  
  
## <a name="input-trace-requirements"></a><span data-ttu-id="74456-104">輸入追蹤需求</span><span class="sxs-lookup"><span data-stu-id="74456-104">Input Trace Requirements</span></span>  
 <span data-ttu-id="74456-105">為了順利重新執行追蹤資料，它必須符合版本和格式的需求，並且包含必要的事件和資料行。</span><span class="sxs-lookup"><span data-stu-id="74456-105">To successfully replay trace data, it must meet the requirements for version and format, and contain the required events and columns.</span></span>  
  
### <a name="input-trace-versions"></a><span data-ttu-id="74456-106">輸入追蹤版本</span><span class="sxs-lookup"><span data-stu-id="74456-106">Input Trace Versions</span></span>  
 <span data-ttu-id="74456-107">Distributed Replay 支援從下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本收集而來的輸入追蹤資料：</span><span class="sxs-lookup"><span data-stu-id="74456-107">Distributed Replay supports input trace data that is collected on the following versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
### <a name="input-trace-formats"></a><span data-ttu-id="74456-108">輸入追蹤格式</span><span class="sxs-lookup"><span data-stu-id="74456-108">Input Trace Formats</span></span>  
 <span data-ttu-id="74456-109">輸入追蹤資料可以採用下列任何格式：</span><span class="sxs-lookup"><span data-stu-id="74456-109">The input trace data can be in any of the following formats:</span></span>  
  
-   <span data-ttu-id="74456-110">具有 `.trc` 副檔名的單一追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="74456-110">A single trace file that has the `.trc` extension.</span></span>  
  
-   <span data-ttu-id="74456-111">一組遵循檔案換用命名規範的換用追蹤檔案，例如：`<TraceFile>.trc`、`<TraceFile>_1.trc`、`<TraceFile>_2.trc`、`<TraceFile>_3.trc`... `<TraceFile>_n.trc`。</span><span class="sxs-lookup"><span data-stu-id="74456-111">A set of rollover trace files that follow the file rollover naming convention, for example: `<TraceFile>.trc`, `<TraceFile>_1.trc`, `<TraceFile>_2.trc`, `<TraceFile>_3.trc`, ... `<TraceFile>_n.trc`.</span></span>  
  
### <a name="input-trace-events-and-columns"></a><span data-ttu-id="74456-112">輸入追蹤事件和資料行</span><span class="sxs-lookup"><span data-stu-id="74456-112">Input Trace Events and Columns</span></span>  
 <span data-ttu-id="74456-113">輸入追蹤資料必須包含特定的事件及資料行，如此 Distributed Replay 才可重新執行。</span><span class="sxs-lookup"><span data-stu-id="74456-113">The input trace data must contain specific events and columns to be replayed by Distributed Replay.</span></span> <span data-ttu-id="74456-114">**中的** TSQL_Replay [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 範本包含所有必要的事件和資料，以及額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="74456-114">The **TSQL_Replay** template in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contains all of the required events and columns, in addition to extra information.</span></span> <span data-ttu-id="74456-115">如需該範本的詳細資訊，請參閱 [重新執行需求](../sql-server-profiler/replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74456-115">For more information about that template, see [Replay Requirements](../sql-server-profiler/replay-requirements.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="74456-116">若您未使用 **TSQL_Replay** 範本來擷取輸入追蹤資料，或不符合輸入追蹤資料的需求，可能會收到未預期的重新執行結果。</span><span class="sxs-lookup"><span data-stu-id="74456-116">If you do not use the **TSQL_Replay** template to capture the input trace data, or if the input trace requirements are not satisfied, you may receive unexpected replay results.</span></span>  
  
 <span data-ttu-id="74456-117">您也可以建立自訂追蹤範本，並使用該範本搭配 Distributed Replay 重新執行事件，但該範本必須包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="74456-117">You can also create a custom trace template and use it to replay events with Distributed Replay, as long as it contains the following events:</span></span>  
  
-   <span data-ttu-id="74456-118">稽核登入</span><span class="sxs-lookup"><span data-stu-id="74456-118">Audit Login</span></span>  
  
-   <span data-ttu-id="74456-119">稽核登出</span><span class="sxs-lookup"><span data-stu-id="74456-119">Audit Logout</span></span>  
  
-   <span data-ttu-id="74456-120">ExistingConnection</span><span class="sxs-lookup"><span data-stu-id="74456-120">ExistingConnection</span></span>  
  
-   <span data-ttu-id="74456-121">RPC Output Parameter</span><span class="sxs-lookup"><span data-stu-id="74456-121">RPC Output Parameter</span></span>  
  
-   <span data-ttu-id="74456-122">RPC:Completed</span><span class="sxs-lookup"><span data-stu-id="74456-122">RPC:Completed</span></span>  
  
-   <span data-ttu-id="74456-123">RPC:Starting</span><span class="sxs-lookup"><span data-stu-id="74456-123">RPC:Starting</span></span>  
  
-   <span data-ttu-id="74456-124">SQL:BatchCompleted</span><span class="sxs-lookup"><span data-stu-id="74456-124">SQL:BatchCompleted</span></span>  
  
-   <span data-ttu-id="74456-125">SQL:BatchStarting</span><span class="sxs-lookup"><span data-stu-id="74456-125">SQL:BatchStarting</span></span>  
  
 <span data-ttu-id="74456-126">如果您要重新執行伺服器端資料指標，下列事件也是必要的：</span><span class="sxs-lookup"><span data-stu-id="74456-126">If you are replaying server-side cursors, the following events are also required:</span></span>  
  
-   <span data-ttu-id="74456-127">CursorClose</span><span class="sxs-lookup"><span data-stu-id="74456-127">CursorClose</span></span>  
  
-   <span data-ttu-id="74456-128">CursorExecute</span><span class="sxs-lookup"><span data-stu-id="74456-128">CursorExecute</span></span>  
  
-   <span data-ttu-id="74456-129">CursorOpen</span><span class="sxs-lookup"><span data-stu-id="74456-129">CursorOpen</span></span>  
  
-   <span data-ttu-id="74456-130">CursorPrepare</span><span class="sxs-lookup"><span data-stu-id="74456-130">CursorPrepare</span></span>  
  
-   <span data-ttu-id="74456-131">CursorUnprepare</span><span class="sxs-lookup"><span data-stu-id="74456-131">CursorUnprepare</span></span>  
  
 <span data-ttu-id="74456-132">如果您要重新執行伺服端 SQL 準備陳述式，下列事件也是必要的：</span><span class="sxs-lookup"><span data-stu-id="74456-132">If you are replaying server-side prepared SQL statements, the following events are also required:</span></span>  
  
-   <span data-ttu-id="74456-133">Exec Prepared SQL</span><span class="sxs-lookup"><span data-stu-id="74456-133">Exec Prepared SQL</span></span>  
  
-   <span data-ttu-id="74456-134">Prepare SQL</span><span class="sxs-lookup"><span data-stu-id="74456-134">Prepare SQL</span></span>  
  
 <span data-ttu-id="74456-135">所有輸入追蹤資料都必須包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="74456-135">All input trace data must contain the following columns:</span></span>  
  
-   <span data-ttu-id="74456-136">Event Class</span><span class="sxs-lookup"><span data-stu-id="74456-136">Event Class</span></span>  
  
-   <span data-ttu-id="74456-137">EventSequence</span><span class="sxs-lookup"><span data-stu-id="74456-137">EventSequence</span></span>  
  
-   <span data-ttu-id="74456-138">TextData</span><span class="sxs-lookup"><span data-stu-id="74456-138">TextData</span></span>  
  
-   <span data-ttu-id="74456-139">應用程式名稱</span><span class="sxs-lookup"><span data-stu-id="74456-139">Application Name</span></span>  
  
-   <span data-ttu-id="74456-140">LoginName</span><span class="sxs-lookup"><span data-stu-id="74456-140">LoginName</span></span>  
  
-   <span data-ttu-id="74456-141">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="74456-141">DatabaseName</span></span>  
  
-   <span data-ttu-id="74456-142">資料庫識別碼</span><span class="sxs-lookup"><span data-stu-id="74456-142">Database ID</span></span>  
  
-   <span data-ttu-id="74456-143">HostName</span><span class="sxs-lookup"><span data-stu-id="74456-143">HostName</span></span>  
  
-   <span data-ttu-id="74456-144">Binary Data</span><span class="sxs-lookup"><span data-stu-id="74456-144">Binary Data</span></span>  
  
-   <span data-ttu-id="74456-145">SPID</span><span class="sxs-lookup"><span data-stu-id="74456-145">SPID</span></span>  
  
-   <span data-ttu-id="74456-146">開始時間</span><span class="sxs-lookup"><span data-stu-id="74456-146">Start Time</span></span>  
  
-   <span data-ttu-id="74456-147">EndTime</span><span class="sxs-lookup"><span data-stu-id="74456-147">EndTime</span></span>  
  
-   <span data-ttu-id="74456-148">IsSystem</span><span class="sxs-lookup"><span data-stu-id="74456-148">IsSystem</span></span>  
  
## <a name="supported-input-trace-and-target-server-combinations"></a><span data-ttu-id="74456-149">支援的輸入追蹤與目標伺服器組合</span><span class="sxs-lookup"><span data-stu-id="74456-149">Supported Input Trace and Target Server Combinations</span></span>  
 <span data-ttu-id="74456-150">下表將列出支援的追蹤資料版本，以及對於每個版本而言，可用來重新執行資料的支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="74456-150">The following table lists the supported versions of trace data, and for each, the supported versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that data can be replayed against.</span></span>  
  
|<span data-ttu-id="74456-151">輸入追蹤資料的版本</span><span class="sxs-lookup"><span data-stu-id="74456-151">Version of Input Trace Data</span></span>|<span data-ttu-id="74456-152">目標伺服器執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援版本</span><span class="sxs-lookup"><span data-stu-id="74456-152">Supported Versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the Target Server Instance</span></span>|  
|---------------------------------|------------------------------------------------------------------------------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="74456-153">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74456-153">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="74456-154">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74456-154">, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="74456-155">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74456-155">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<span data-ttu-id="74456-156">, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74456-156">, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
  
## <a name="operating-system-requirements"></a><span data-ttu-id="74456-157">作業系統需求</span><span class="sxs-lookup"><span data-stu-id="74456-157">Operating System Requirements</span></span>  
 <span data-ttu-id="74456-158">支援執行管理工具以及控制器和用戶端服務的作業系統，與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體相同。</span><span class="sxs-lookup"><span data-stu-id="74456-158">Supported operating systems for running the administration tool and the controller and client services is the same as your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="74456-159">如需您的實例支援哪些作業系統的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[安裝 SQL Server 2014 的硬體和軟體需求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="74456-159">For more information about which operating systems are supported for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
 <span data-ttu-id="74456-160">x86 及 x64 作業系統皆支援 Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="74456-160">Distributed Replay features are supported on both x86-based and x64-based operating systems.</span></span> <span data-ttu-id="74456-161">若為 x64 架構作業系統，只支援 Windows on Windows (WOW) 模式。</span><span class="sxs-lookup"><span data-stu-id="74456-161">For x64-based operating systems, only Windows on Windows (WOW) mode is supported.</span></span>  
  
## <a name="installation-limitations"></a><span data-ttu-id="74456-162">安裝限制</span><span class="sxs-lookup"><span data-stu-id="74456-162">Installation Limitations</span></span>  
 <span data-ttu-id="74456-163">對於各項 Distributed Replay 功能，每部電腦皆只能夠安裝一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="74456-163">Any one computer can only have a single instance of each Distributed Replay feature installed.</span></span> <span data-ttu-id="74456-164">下表列出單一 Distributed Replay 環境中對於各項功能所能夠安裝的數量。</span><span class="sxs-lookup"><span data-stu-id="74456-164">The following table lists how many installations of each feature are allowed in a single Distributed Replay environment.</span></span>  
  
|<span data-ttu-id="74456-165">Distributed Replay 功能</span><span class="sxs-lookup"><span data-stu-id="74456-165">Distributed Replay Feature</span></span>|<span data-ttu-id="74456-166">每個重新執行環境的最大安裝數目</span><span class="sxs-lookup"><span data-stu-id="74456-166">Maximum Installations Per Replay Environment</span></span>|  
|--------------------------------|--------------------------------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="74456-167">Distributed Replay Controller 服務</span><span class="sxs-lookup"><span data-stu-id="74456-167">Distributed Replay controller service</span></span>|<span data-ttu-id="74456-168">1</span><span class="sxs-lookup"><span data-stu-id="74456-168">1</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="74456-169">Distributed Replay Client 服務</span><span class="sxs-lookup"><span data-stu-id="74456-169">Distributed Replay client service</span></span>|<span data-ttu-id="74456-170">16 (實體或虛擬電腦)</span><span class="sxs-lookup"><span data-stu-id="74456-170">16 (physical or virtual computers)</span></span>|  
|<span data-ttu-id="74456-171">管理工具</span><span class="sxs-lookup"><span data-stu-id="74456-171">Administration tool</span></span>|<span data-ttu-id="74456-172">無限制</span><span class="sxs-lookup"><span data-stu-id="74456-172">Unlimited</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="74456-173">雖然單一電腦只能安裝一個管理工具的執行個體，不過您可以啟動多個管理工具的執行個體。</span><span class="sxs-lookup"><span data-stu-id="74456-173">Although only one instance of the administration tool can be installed on a single computer, you can start multiple instances of the administration tool.</span></span> <span data-ttu-id="74456-174">從多個管理工具發出的命令會按照系統接收的順序來解析。</span><span class="sxs-lookup"><span data-stu-id="74456-174">Commands issued from multiple administration tools are resolved in the order in which they are received.</span></span>  
  
## <a name="data-access-provider"></a><span data-ttu-id="74456-175">資料存取提供者</span><span class="sxs-lookup"><span data-stu-id="74456-175">Data Access Provider</span></span>  
 <span data-ttu-id="74456-176">Distributed Replay 只支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 資料存取提供者。</span><span class="sxs-lookup"><span data-stu-id="74456-176">Distributed Replay only supports the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC data access provider.</span></span>  
  
## <a name="target-server-preparation-requirements"></a><span data-ttu-id="74456-177">目標伺服器準備需求</span><span class="sxs-lookup"><span data-stu-id="74456-177">Target Server Preparation Requirements</span></span>  
 <span data-ttu-id="74456-178">我們建議您將目標伺服器放置於測試環境中。</span><span class="sxs-lookup"><span data-stu-id="74456-178">We recommend that the target server be located in a test environment.</span></span> <span data-ttu-id="74456-179">若要針對與原始記錄不同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體重新執行追蹤資料，請確定已經對目標伺服器完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="74456-179">To replay trace data against a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] than it was originally recorded, make sure that the following has been done to the target server:</span></span>  
  
-   <span data-ttu-id="74456-180">追蹤資料中包含的所有登入與使用者都必須存在目標伺服器的相同資料庫中。</span><span class="sxs-lookup"><span data-stu-id="74456-180">All logins and users that are contained in the trace data must be present in the same database on the target server.</span></span>  
  
-   <span data-ttu-id="74456-181">目標伺服器上的所有登入與使用者，其權限必須與在原始伺服器上擁有的權限相同。</span><span class="sxs-lookup"><span data-stu-id="74456-181">All logins and users on the target server must have the same permissions they had on the original server.</span></span>  
  
-   <span data-ttu-id="74456-182">目標上的資料庫識別碼必須與來源上的一樣。</span><span class="sxs-lookup"><span data-stu-id="74456-182">The database IDs on the target ideally should be the same as those on the source.</span></span> <span data-ttu-id="74456-183">不過，如果不相同，若追蹤內有 **DatabaseName** 的話， 就可以據以執行比對作業。</span><span class="sxs-lookup"><span data-stu-id="74456-183">However, if they are not the same, matching can be performed based on **DatabaseName** if it is present in the trace.</span></span>  
  
-   <span data-ttu-id="74456-184">追蹤資料中包含之每個登入的預設資料庫必須設成 (在目標伺服器上) 登入的個別目標資料庫。</span><span class="sxs-lookup"><span data-stu-id="74456-184">The default database for each login that is contained in the trace data must be set (on the target server) to the respective target database of the login.</span></span> <span data-ttu-id="74456-185">例如，要重新執行的追蹤資料包含 **Fred**登入的活動，其位於原始 **執行個體的** Fred_Db [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫中。</span><span class="sxs-lookup"><span data-stu-id="74456-185">For example, the trace data to be replayed contains activity for the login, **Fred**, in the database **Fred_Db** on the original instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74456-186">因此，在目標伺服器上， **Fred**登入的預設資料庫必須設成符合 **Fred_Db** 的資料庫 (即使資料庫名稱不同)。</span><span class="sxs-lookup"><span data-stu-id="74456-186">Therefore, on the target server, the default database for the login, **Fred**, must be set to the database that matches **Fred_Db** (even if the database name is different).</span></span> <span data-ttu-id="74456-187">若要設定登入的預設資料庫，可使用 `sp_defaultdb` 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="74456-187">To set the default database of the login, use the `sp_defaultdb` system stored procedure.</span></span>  
  
 <span data-ttu-id="74456-188">重新執行與找不到或不正確之登入相關的事件，會造成重新執行錯誤，但重新執行作業仍會繼續。</span><span class="sxs-lookup"><span data-stu-id="74456-188">Replaying events associated with missing or incorrect logins results in replay errors, but the replay operation continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74456-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74456-189">See Also</span></span>  
 <span data-ttu-id="74456-190">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="74456-190">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="74456-191">[Distributed Replay 安全性](distributed-replay-security.md) </span><span class="sxs-lookup"><span data-stu-id="74456-191">[Distributed Replay Security](distributed-replay-security.md) </span></span>  
 [<span data-ttu-id="74456-192">安裝 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="74456-192">Install Distributed Replay</span></span>](install-distributed-replay-overview.md)  
  
  
