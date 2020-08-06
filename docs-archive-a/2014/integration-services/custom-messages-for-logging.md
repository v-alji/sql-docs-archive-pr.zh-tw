---
title: 記錄的自訂訊息 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], custom
- writing log entries
- SSIS packages, logs
- custom messages for logging [Integration Services]
ms.assetid: 3c74bba9-02b7-4bf5-bad5-19278b680730
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2b9f450c74ef6d46876adfde45729c71b3262449
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596212"
---
# <a name="custom-messages-for-logging"></a><span data-ttu-id="c269c-102">自訂訊息以進行記錄</span><span class="sxs-lookup"><span data-stu-id="c269c-102">Custom Messages for Logging</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="c269c-103">提供一組豐富的自訂事件，可以為封裝和許多工作寫入記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-103">provides a rich set of custom events for writing log entries for packages and many tasks.</span></span> <span data-ttu-id="c269c-104">您可以使用這些項目，透過記錄預先定義事件或使用者自訂訊息，來儲存關於執行進度、結果和問題的詳細資訊，以供稍後分析。</span><span class="sxs-lookup"><span data-stu-id="c269c-104">You can use these entries to save detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="c269c-105">比方說，您可以記錄大量插入開始和結束的時間，以便識別封裝執行時的效能問題。</span><span class="sxs-lookup"><span data-stu-id="c269c-105">For example, you can record when a bulk insert begins and ends to identify performance issues when the package runs.</span></span>  
  
 <span data-ttu-id="c269c-106">自訂記錄項目是一組與可用於封裝以及所有容器和工作的標準記錄事件不同的項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-106">The custom log entries are a different set of entries than the set of standard logging events that are available for packages and all containers and tasks.</span></span> <span data-ttu-id="c269c-107">自訂記錄項目可以用來擷取與封裝中特定工作相關的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-107">The custom log entries are tailored to capture useful information about a specific task in a package.</span></span> <span data-ttu-id="c269c-108">例如，「執行 SQL」工作記錄的其中一個自訂記錄項目會在記錄檔中記錄該工作所執行的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c269c-108">For example, one of the custom log entries for the Execute SQL task records the SQL statement that the task executes in the log.</span></span>  
  
 <span data-ttu-id="c269c-109">所有的記錄項目都包含日期和時間資訊，包括封裝開始和完成時自動寫入的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-109">All log entries include date and time information, including the log entries that are automatically written when a package begins and finishes.</span></span> <span data-ttu-id="c269c-110">許多記錄事件都會將多個項目寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c269c-110">Many of the log events write multiple entries to the log.</span></span> <span data-ttu-id="c269c-111">當事件具有不同的階段時，通常就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="c269c-111">This typically occurs when the event has different phases.</span></span> <span data-ttu-id="c269c-112">例如，`ExecuteSQLExecutingQuery` 記錄事件會寫入三個項目：在工作取得資料庫連接之後寫入一個項目、在工作開始準備 SQL 陳述式之後寫入另一個項目，然後在 SQL 陳述式執行完成之後再寫入一個項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-112">For example, the `ExecuteSQLExecutingQuery` log event writes three entries: one entry after the task acquires a connection to the database, another after the task starts to prepare the SQL statement, and one more after the execution of the SQL statement is completed.</span></span>  
  
 <span data-ttu-id="c269c-113">下列 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 物件具有自訂記錄項目：</span><span class="sxs-lookup"><span data-stu-id="c269c-113">The following [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects have custom log entries:</span></span>  
  
 [<span data-ttu-id="c269c-114">套件</span><span class="sxs-lookup"><span data-stu-id="c269c-114">Package</span></span>](#Package)  
  
 [<span data-ttu-id="c269c-115">大量插入工作</span><span class="sxs-lookup"><span data-stu-id="c269c-115">Bulk Insert Task</span></span>](#BulkInsert)  
  
 [<span data-ttu-id="c269c-116">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="c269c-116">Data Flow Task</span></span>](#DataFlow)  
  
 [<span data-ttu-id="c269c-117">執行 DTS 2000 工作</span><span class="sxs-lookup"><span data-stu-id="c269c-117">Execute DTS 2000 Task</span></span>](#ExecuteDTS200)  
  
 [<span data-ttu-id="c269c-118">執行處理工作</span><span class="sxs-lookup"><span data-stu-id="c269c-118">Execute Process Task</span></span>](#ExecuteProcess)  
  
 [<span data-ttu-id="c269c-119">執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="c269c-119">Execute SQL Task</span></span>](#ExecuteSQL)  
  
 [<span data-ttu-id="c269c-120">檔案系統工作</span><span class="sxs-lookup"><span data-stu-id="c269c-120">File System Task</span></span>](#FileSystem)  
  
 [<span data-ttu-id="c269c-121">FTP 工作</span><span class="sxs-lookup"><span data-stu-id="c269c-121">FTP Task</span></span>](#FTP)  
  
 [<span data-ttu-id="c269c-122">訊息佇列工作</span><span class="sxs-lookup"><span data-stu-id="c269c-122">Message Queue Task</span></span>](#MessageQueue)  
  
 [<span data-ttu-id="c269c-123">指令碼工作</span><span class="sxs-lookup"><span data-stu-id="c269c-123">Script Task</span></span>](#Script)  
  
 [<span data-ttu-id="c269c-124">傳送電子郵件工作</span><span class="sxs-lookup"><span data-stu-id="c269c-124">Send Mail Task</span></span>](#SendMail)  
  
 [<span data-ttu-id="c269c-125">傳輸資料庫工作</span><span class="sxs-lookup"><span data-stu-id="c269c-125">Transfer Database Task</span></span>](#TransferDatabase)  
  
 [<span data-ttu-id="c269c-126">傳輸錯誤訊息工作</span><span class="sxs-lookup"><span data-stu-id="c269c-126">Transfer Error Messages Task</span></span>](#TransferErrorMessages)  
  
 [<span data-ttu-id="c269c-127">傳輸作業工作</span><span class="sxs-lookup"><span data-stu-id="c269c-127">Transfer Jobs Task</span></span>](#TransferJobs)  
  
 [<span data-ttu-id="c269c-128">傳輸登入工作</span><span class="sxs-lookup"><span data-stu-id="c269c-128">Transfer Logins Task</span></span>](#TransferLogins)  
  
 [<span data-ttu-id="c269c-129">傳輸主要預存程序工作</span><span class="sxs-lookup"><span data-stu-id="c269c-129">Transfer Master Stored Procedures Task</span></span>](#TransferMasterStoredProcedures)  
  
 [<span data-ttu-id="c269c-130">傳輸 SQL 伺服器物件工作</span><span class="sxs-lookup"><span data-stu-id="c269c-130">Transfer SQL Server Objects Task</span></span>](#TransferSQLServerObjects)  
  
 [<span data-ttu-id="c269c-131">Web 服務工作</span><span class="sxs-lookup"><span data-stu-id="c269c-131">Web Services Task</span></span>](#WebServices)  
  
 [<span data-ttu-id="c269c-132">WMI 資料讀取器工作</span><span class="sxs-lookup"><span data-stu-id="c269c-132">WMI Data Reader Task</span></span>](#WMIDataReader)  
  
 [<span data-ttu-id="c269c-133">WMI 事件監看員工作</span><span class="sxs-lookup"><span data-stu-id="c269c-133">WMI Event Watcher Task</span></span>](#WMIEventWatcher)  
  
 [<span data-ttu-id="c269c-134">XML 工作</span><span class="sxs-lookup"><span data-stu-id="c269c-134">XML Task</span></span>](#XML)  
  
## <a name="log-entries"></a><span data-ttu-id="c269c-135">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-135">Log Entries</span></span>  
  
###  <a name="package"></a><a name="Package"></a> <span data-ttu-id="c269c-136">封裝</span><span class="sxs-lookup"><span data-stu-id="c269c-136">Package</span></span>  
 <span data-ttu-id="c269c-137">下表列出封裝的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-137">The following table lists the custom log entries for packages.</span></span>  
  
|<span data-ttu-id="c269c-138">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-138">Log entry</span></span>|<span data-ttu-id="c269c-139">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-139">Description</span></span>|  
|---------------|-----------------|  
|`PackageStart`|<span data-ttu-id="c269c-140">指出封裝已經開始執行。</span><span class="sxs-lookup"><span data-stu-id="c269c-140">Indicates that the package began to run.</span></span><br /><br /> <span data-ttu-id="c269c-141">注意：此記錄項目會自動寫入記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="c269c-141">Note: This log entry is automatically written to the log.</span></span> <span data-ttu-id="c269c-142">您無法排除它。</span><span class="sxs-lookup"><span data-stu-id="c269c-142">You cannot exclude it.</span></span>|  
|`PackageEnd`|<span data-ttu-id="c269c-143">指出封裝已經完成。</span><span class="sxs-lookup"><span data-stu-id="c269c-143">Indicates that the package completed.</span></span><br /><br /> <span data-ttu-id="c269c-144">注意：此記錄項目會自動寫入記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="c269c-144">Note: This log entry is automatically written to the log.</span></span> <span data-ttu-id="c269c-145">您無法排除它。</span><span class="sxs-lookup"><span data-stu-id="c269c-145">You cannot exclude it.</span></span>|  
|`Diagnostic`|<span data-ttu-id="c269c-146">提供影響封裝執行之系統組態的相關資訊，例如可以同時執行的可執行檔數目。</span><span class="sxs-lookup"><span data-stu-id="c269c-146">Provides information about the system configuration that affects package execution such as the number executables that can be run concurrently.</span></span><br /><br /> <span data-ttu-id="c269c-147">`Diagnostic` 記錄項目也包括呼叫外部資料提供者之前和之後的項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-147">The `Diagnostic` log entry also includes before and after entries for calls to external data providers.</span></span> <span data-ttu-id="c269c-148">如需詳細資訊，請參閱 [疑難排解工具封裝連接](troubleshooting/troubleshooting-tools-for-package-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="c269c-148">For more information, see [Troubleshooting Tools Package Connectivity](troubleshooting/troubleshooting-tools-for-package-connectivity.md).</span></span>|  
  
###  <a name="bulk-insert-task"></a><a name="BulkInsert"></a> <span data-ttu-id="c269c-149">大量插入工作</span><span class="sxs-lookup"><span data-stu-id="c269c-149">Bulk Insert Task</span></span>  
 <span data-ttu-id="c269c-150">下表列出「大量插入」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-150">The following table lists the custom log entries for the Bulk Insert task.</span></span>  
  
|<span data-ttu-id="c269c-151">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-151">Log entry</span></span>|<span data-ttu-id="c269c-152">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-152">Description</span></span>|  
|---------------|-----------------|  
|`DTSBulkInsertTaskBegin`|<span data-ttu-id="c269c-153">指出大量插入已經開始。</span><span class="sxs-lookup"><span data-stu-id="c269c-153">Indicates that the bulk insert began.</span></span>|  
|`DTSBulkInsertTaskEnd`|<span data-ttu-id="c269c-154">指出大量插入已經完成。</span><span class="sxs-lookup"><span data-stu-id="c269c-154">Indicates that the bulk insert finished.</span></span>|  
|`DTSBulkInsertTaskInfos`|<span data-ttu-id="c269c-155">提供有關工作的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-155">Provides descriptive information about the task.</span></span>|  
  
###  <a name="data-flow-task"></a><a name="DataFlow"></a> <span data-ttu-id="c269c-156">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="c269c-156">Data Flow Task</span></span>  
 <span data-ttu-id="c269c-157">下表列出「資料流程」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-157">The following table lists the custom log entries for the Data Flow task.</span></span>  
  
|<span data-ttu-id="c269c-158">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-158">Log entry</span></span>|<span data-ttu-id="c269c-159">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-159">Description</span></span>|  
|---------------|-----------------|  
|`BufferSizeTuning`|<span data-ttu-id="c269c-160">指出資料流程工作已經變更緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="c269c-160">Indicates that the Data Flow task changed the size of the buffer.</span></span> <span data-ttu-id="c269c-161">記錄項目會描述大小變更的原因，並列出暫存的新緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="c269c-161">The log entry describes the reasons for the size change and lists the temporary new buffer size.</span></span>|  
|`OnPipelinePostEndOfRowset`|<span data-ttu-id="c269c-162">表示已經為元件指定了資料列集結尾信號，此信號是由 `ProcessInput` 方法的最後一次呼叫所設定。</span><span class="sxs-lookup"><span data-stu-id="c269c-162">Denotes that a component has been given its end-of-rowset signal, which is set by the last call of the `ProcessInput` method.</span></span> <span data-ttu-id="c269c-163">處理輸入之資料流程中的每個元件都會寫入一個項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-163">An entry is written for each component in the data flow that processes input.</span></span> <span data-ttu-id="c269c-164">項目中包含元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c269c-164">The entry includes the name of the component.</span></span>|  
|`OnPipelinePostPrimeOutput`|<span data-ttu-id="c269c-165">指出元件已經完成 `PrimeOutput` 方法的最後一次呼叫。</span><span class="sxs-lookup"><span data-stu-id="c269c-165">Indicates that the component has completed its last call to the `PrimeOutput` method.</span></span> <span data-ttu-id="c269c-166">根據資料流程而定，可能會寫入多個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-166">Depending on the data flow, multiple log entries may be written.</span></span> <span data-ttu-id="c269c-167">如果元件是來源，這表示該元件已經完成處理資料列。</span><span class="sxs-lookup"><span data-stu-id="c269c-167">If the component is a source, this means that the component has finished processing rows.</span></span>|  
|`OnPipelinePreEndOfRowset`|<span data-ttu-id="c269c-168">指出元件即將接收其資料列集結尾信號，此信號是由 `ProcessInput` 方法的最後一次呼叫所設定。</span><span class="sxs-lookup"><span data-stu-id="c269c-168">Indicates that a component is about to receive its end-of-rowset signal, which is set by the last call of the `ProcessInput` method.</span></span> <span data-ttu-id="c269c-169">處理輸入之資料流程中的每個元件都會寫入一個項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-169">An entry is written for each component in the data flow that processes input.</span></span> <span data-ttu-id="c269c-170">項目中包含元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c269c-170">The entry includes the name of the component.</span></span>|  
|`OnPipelinePrePrimeOutput`|<span data-ttu-id="c269c-171">指出元件即將從 `PrimeOutput` 方法接收其呼叫。</span><span class="sxs-lookup"><span data-stu-id="c269c-171">Indicates that the component is about to receive its call from the `PrimeOutput` method.</span></span> <span data-ttu-id="c269c-172">根據資料流程而定，可能會寫入多個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-172">Depending on the data flow, multiple log entries may be written.</span></span>|  
|`OnPipelineRowsSent`|<span data-ttu-id="c269c-173">報告由 `ProcessInput` 方法之呼叫提供給元件輸入的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="c269c-173">Reports the number of rows provided to a component input by a call to the `ProcessInput` method.</span></span> <span data-ttu-id="c269c-174">記錄項目會包含元件名稱。</span><span class="sxs-lookup"><span data-stu-id="c269c-174">The log entry includes the component name.</span></span>|  
|`PipelineBufferLeak`|<span data-ttu-id="c269c-175">提供在緩衝區管理員停止之後使緩衝區保持運作之任何元件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-175">Provides information about any component that kept buffers alive after the buffer manager goes away.</span></span> <span data-ttu-id="c269c-176">這表示緩衝區資源並未釋放，而可能導致記憶體遺漏。</span><span class="sxs-lookup"><span data-stu-id="c269c-176">This means that buffers resources were not released and may cause memory leaks.</span></span> <span data-ttu-id="c269c-177">記錄項目會提供元件的名稱和緩衝區的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c269c-177">The log entry provides the name of the component and the ID of the buffer.</span></span>|  
|`PipelineExecutionPlan`|<span data-ttu-id="c269c-178">報告資料流程的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="c269c-178">Reports the execution plan of the data flow.</span></span> <span data-ttu-id="c269c-179">此項目提供如何將緩衝區傳送至元件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-179">It provides information about how buffers will be sent to components.</span></span> <span data-ttu-id="c269c-180">這項資訊結合 PipelineExecutionTrees 項目，描述工作內部所發生的情況。</span><span class="sxs-lookup"><span data-stu-id="c269c-180">This information, in combination with the PipelineExecutionTrees entry, describes what is occurring in the task.</span></span>|  
|`PipelineExecutionTrees`|<span data-ttu-id="c269c-181">報告資料流程中的配置執行樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="c269c-181">Reports the execution trees of the layout in the data flow.</span></span> <span data-ttu-id="c269c-182">資料流程引擎的排程器使用這些樹狀目錄來建立資料流程的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="c269c-182">The scheduler of the data flow engine use the trees to build the execution plan of the data flow.</span></span>|  
|`PipelineInitialization`|<span data-ttu-id="c269c-183">提供有關工作的初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-183">Provides initialization information about the task.</span></span> <span data-ttu-id="c269c-184">這項資訊包括作為 BLOB 資料暫存儲存位置使用的目錄、預設緩衝區大小，以及緩衝區中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="c269c-184">This information includes the directories to use for temporary storage of BLOB data, the default buffer size, and the number of rows in a buffer.</span></span> <span data-ttu-id="c269c-185">根據資料流程工作的組態而定，可能會寫入多個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-185">Depending on the configuration of the Data Flow task, multiple log entries may be written.</span></span>|  
  
###  <a name="execute-dts-2000-task"></a><a name="ExecuteDTS200"></a> <span data-ttu-id="c269c-186">執行 DTS 2000 工作</span><span class="sxs-lookup"><span data-stu-id="c269c-186">Execute DTS 2000 Task</span></span>  
 <span data-ttu-id="c269c-187">下表列出「執行 DTS 2000」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-187">The following table lists the custom log entries for the Execute DTS 2000 task.</span></span>  
  
|<span data-ttu-id="c269c-188">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-188">Log entry</span></span>|<span data-ttu-id="c269c-189">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-189">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteDTS80PackageTaskBegin`|<span data-ttu-id="c269c-190">指出工作已經開始執行 DTS 2000 封裝。</span><span class="sxs-lookup"><span data-stu-id="c269c-190">Indicates that the task began to run a DTS 2000 package.</span></span>|  
|`ExecuteDTS80PackageTaskEnd`|<span data-ttu-id="c269c-191">指出工作已經完成。</span><span class="sxs-lookup"><span data-stu-id="c269c-191">Indicates that the task finished.</span></span><br /><br /> <span data-ttu-id="c269c-192">注意：DTS 2000 封裝可能會在工作結束之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="c269c-192">Note: The DTS 2000 package may continue to run after the task ends.</span></span>|  
|`ExecuteDTS80PackageTaskTaskInfo`|<span data-ttu-id="c269c-193">提供有關工作的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-193">Provides descriptive information about the task.</span></span>|  
|`ExecuteDTS80PackageTaskTaskResult`|<span data-ttu-id="c269c-194">報告工作執行之 DTS 2000 封裝的執行結果。</span><span class="sxs-lookup"><span data-stu-id="c269c-194">Reports the execution result of the DTS 2000 package that the task ran.</span></span>|  
  
###  <a name="execute-process-task"></a><a name="ExecuteProcess"></a> <span data-ttu-id="c269c-195">執行處理工作</span><span class="sxs-lookup"><span data-stu-id="c269c-195">Execute Process Task</span></span>  
 <span data-ttu-id="c269c-196">下表列出「執行處理」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-196">The following table lists the custom log entries for the Execute Process task.</span></span>  
  
|<span data-ttu-id="c269c-197">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-197">Log entry</span></span>|<span data-ttu-id="c269c-198">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-198">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|<span data-ttu-id="c269c-199">提供工作設定執行之可執行檔的執行處理相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-199">Provides information about the process of running the executable that the task is configured to run.</span></span><br /><br /> <span data-ttu-id="c269c-200">將會寫入兩個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-200">Two log entries are written.</span></span> <span data-ttu-id="c269c-201">其中一個包含工作執行之可執行檔的名稱和位置相關資訊，另一個項目則記錄可執行檔的結束。</span><span class="sxs-lookup"><span data-stu-id="c269c-201">One contains information about the name and location of the executable that the task runs, and the other records the exit from the executable.</span></span>|  
|`ExecuteProcessVariableRouting`|<span data-ttu-id="c269c-202">提供有關哪些變數會傳到可執行檔之輸入和輸出的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-202">Provides information about which variables are routed to the input and outputs of the executable.</span></span> <span data-ttu-id="c269c-203">將會寫入 stdin (輸入)、stdout (輸出) 和 stderr (錯誤輸出) 的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-203">Log entries are written for stdin (the input), stdout (the output), and stderr (the error output).</span></span>|  
  
###  <a name="execute-sql-task"></a><a name="ExecuteSQL"></a> <span data-ttu-id="c269c-204">執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="c269c-204">Execute SQL Task</span></span>  
 <span data-ttu-id="c269c-205">下表描述「執行 SQL」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-205">The following table describes the custom log entry for the Execute SQL task.</span></span>  
  
|<span data-ttu-id="c269c-206">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-206">Log entry</span></span>|<span data-ttu-id="c269c-207">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-207">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|<span data-ttu-id="c269c-208">提供 SQL 陳述式執行階段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-208">Provides information about the execution phases of the SQL statement.</span></span> <span data-ttu-id="c269c-209">寫入記錄項目的時機包括在工作取得資料庫連接時、在工作開始準備 SQL 陳述式時，以及在 SQL 陳述式執行完成之後。</span><span class="sxs-lookup"><span data-stu-id="c269c-209">Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed.</span></span> <span data-ttu-id="c269c-210">準備階段的記錄項目包含工作所使用的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c269c-210">The log entry for the prepare phase includes the SQL statement that the task uses.</span></span>|  
  
###  <a name="file-system-task"></a><a name="FileSystem"></a> <span data-ttu-id="c269c-211">檔案系統工作</span><span class="sxs-lookup"><span data-stu-id="c269c-211">File System Task</span></span>  
 <span data-ttu-id="c269c-212">下表描述「檔案系統」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-212">The following table describes the custom log entry for the File System task.</span></span>  
  
|<span data-ttu-id="c269c-213">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-213">Log entry</span></span>|<span data-ttu-id="c269c-214">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-214">Description</span></span>|  
|---------------|-----------------|  
|`FileSystemOperation`|<span data-ttu-id="c269c-215">報告工作執行的作業。</span><span class="sxs-lookup"><span data-stu-id="c269c-215">Reports the operation that the task performs.</span></span> <span data-ttu-id="c269c-216">記錄項目會在檔案系統作業開始時寫入，項目中包含有關來源和目的地的資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-216">The log entry is written when the file system operation starts and includes information about the source and destination.</span></span>|  
  
###  <a name="ftp-task"></a><a name="FTP"></a> <span data-ttu-id="c269c-217">FTP 工作</span><span class="sxs-lookup"><span data-stu-id="c269c-217">FTP Task</span></span>  
 <span data-ttu-id="c269c-218">下表列出 FTP 工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-218">The following table lists the custom log entries for the FTP task.</span></span>  
  
|<span data-ttu-id="c269c-219">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-219">Log entry</span></span>|<span data-ttu-id="c269c-220">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-220">Description</span></span>|  
|---------------|-----------------|  
|`FTPConnectingToServer`|<span data-ttu-id="c269c-221">指出工作已經起始與 FTP 伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="c269c-221">Indicates that the task initiated a connection to the FTP server.</span></span>|  
|`FTPOperation`|<span data-ttu-id="c269c-222">報告工作執行之 FTP 作業的開始及其類型。</span><span class="sxs-lookup"><span data-stu-id="c269c-222">Reports the beginning of and the type of FTP operation that the task performs.</span></span>|  
  
###  <a name="message-queue-task"></a><a name="MessageQueue"></a> <span data-ttu-id="c269c-223">訊息佇列工作</span><span class="sxs-lookup"><span data-stu-id="c269c-223">Message Queue Task</span></span>  
 <span data-ttu-id="c269c-224">下表列出「訊息佇列」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-224">The following table lists the custom log entries for the Message Queue task.</span></span>  
  
|<span data-ttu-id="c269c-225">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-225">Log entry</span></span>|<span data-ttu-id="c269c-226">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-226">Description</span></span>|  
|---------------|-----------------|  
|`MSMQAfterOpen`|<span data-ttu-id="c269c-227">指出工作已經完成開啟訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="c269c-227">Indicates that the task finished opening the message queue.</span></span>|  
|`MSMQBeforeOpen`|<span data-ttu-id="c269c-228">指出工作已經開始開啟訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="c269c-228">Indicates that the task began to open the message queue.</span></span>|  
|`MSMQBeginReceive`|<span data-ttu-id="c269c-229">指出工作已經開始接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c269c-229">Indicates that the task began to receive a message.</span></span>|  
|`MSMQBeginSend`|<span data-ttu-id="c269c-230">指出工作已經開始傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="c269c-230">Indicates that the task began to send a message.</span></span>|  
|`MSMQEndReceive`|<span data-ttu-id="c269c-231">指出工作已經完成接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c269c-231">Indicates that the task finished receiving a message.</span></span>|  
|`MSMQEndSend`|<span data-ttu-id="c269c-232">指出工作已經完成傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="c269c-232">Indicates that the task finished sending a message</span></span>|  
|`MSMQTaskInfo`|<span data-ttu-id="c269c-233">提供有關工作的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-233">Provides descriptive information about the task.</span></span>|  
|`MSMQTaskTimeOut`|<span data-ttu-id="c269c-234">指出工作已經逾時。</span><span class="sxs-lookup"><span data-stu-id="c269c-234">Indicates that the task timed out.</span></span>|  
  
###  <a name="script-task"></a><a name="Script"></a> <span data-ttu-id="c269c-235">指令碼工作</span><span class="sxs-lookup"><span data-stu-id="c269c-235">Script Task</span></span>  
 <span data-ttu-id="c269c-236">下表描述「指令碼」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-236">The following table describes the custom log entry for the Script task.</span></span>  
  
|<span data-ttu-id="c269c-237">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-237">Log entry</span></span>|<span data-ttu-id="c269c-238">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-238">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="c269c-239">報告在指令碼內實作記錄的結果。</span><span class="sxs-lookup"><span data-stu-id="c269c-239">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="c269c-240">每次呼叫 `Log` 物件的 `Dts` 方法時，都會寫入記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-240">A log entry is written for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="c269c-241">項目會在程式碼執行時寫入。</span><span class="sxs-lookup"><span data-stu-id="c269c-241">The entry is written when the code is run.</span></span> <span data-ttu-id="c269c-242">如需詳細資訊，請參閱 [Logging in the Script Task](extending-packages-scripting/task/logging-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="c269c-242">For more information, see [Logging in the Script Task](extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
###  <a name="send-mail-task"></a><a name="SendMail"></a> <span data-ttu-id="c269c-243">傳送郵件工作</span><span class="sxs-lookup"><span data-stu-id="c269c-243">Send Mail Task</span></span>  
 <span data-ttu-id="c269c-244">下表列出「傳送郵件」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-244">The following table lists the custom log entries for the Send Mail task.</span></span>  
  
|<span data-ttu-id="c269c-245">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-245">Log entry</span></span>|<span data-ttu-id="c269c-246">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-246">Description</span></span>|  
|---------------|-----------------|  
|`SendMailTaskBegin`|<span data-ttu-id="c269c-247">指出工作已經開始傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="c269c-247">Indicates that the task began to send an e-mail message.</span></span>|  
|`SendMailTaskEnd`|<span data-ttu-id="c269c-248">指出工作已經完成傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="c269c-248">Indicates that the task finished sending an e-mail message.</span></span>|  
|`SendMailTaskInfo`|<span data-ttu-id="c269c-249">提供有關工作的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-249">Provides descriptive information about the task.</span></span>|  
  
###  <a name="transfer-database-task"></a><a name="TransferDatabase"></a> <span data-ttu-id="c269c-250">傳送資料庫工作</span><span class="sxs-lookup"><span data-stu-id="c269c-250">Transfer Database Task</span></span>  
 <span data-ttu-id="c269c-251">下表列出「傳送資料庫」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-251">The following table lists the custom log entries for the Transfer Database task.</span></span>  
  
|<span data-ttu-id="c269c-252">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-252">Log entry</span></span>|<span data-ttu-id="c269c-253">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-253">Description</span></span>|  
|---------------|-----------------|  
|`SourceDB`|<span data-ttu-id="c269c-254">指定工作所複製的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c269c-254">Specifies the database that the task copied.</span></span>|  
|`SourceSQLServer`|<span data-ttu-id="c269c-255">指定從中複製資料庫的電腦。</span><span class="sxs-lookup"><span data-stu-id="c269c-255">Specifies the computer from which the database was copied.</span></span>|  
  
###  <a name="transfer-error-messages-task"></a><a name="TransferErrorMessages"></a> <span data-ttu-id="c269c-256">傳送錯誤訊息工作</span><span class="sxs-lookup"><span data-stu-id="c269c-256">Transfer Error Messages Task</span></span>  
 <span data-ttu-id="c269c-257">下表列出「傳送錯誤訊息」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-257">The following table lists the custom log entries for the Transfer Error Messages task.</span></span>  
  
|<span data-ttu-id="c269c-258">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-258">Log entry</span></span>|<span data-ttu-id="c269c-259">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-259">Description</span></span>|  
|---------------|-----------------|  
|`TransferErrorMessagesTaskFinishedTransferringObjects`|<span data-ttu-id="c269c-260">指出工作已經完成傳送錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c269c-260">Indicates that the task finished transferring error messages.</span></span>|  
|`TransferErrorMessagesTaskStartTransferringObjects`|<span data-ttu-id="c269c-261">指出工作已經開始傳送錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c269c-261">Indicates that the task started to transfer error messages.</span></span>|  
  
###  <a name="transfer-jobs-task"></a><a name="TransferJobs"></a> <span data-ttu-id="c269c-262">傳送作業工作</span><span class="sxs-lookup"><span data-stu-id="c269c-262">Transfer Jobs Task</span></span>  
 <span data-ttu-id="c269c-263">下表列出「傳送作業」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-263">The following table lists the custom log entries for the Transfer Jobs task.</span></span>  
  
|<span data-ttu-id="c269c-264">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-264">Log entry</span></span>|<span data-ttu-id="c269c-265">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-265">Description</span></span>|  
|---------------|-----------------|  
|`TransferJobsTaskFinishedTransferringObjects`|<span data-ttu-id="c269c-266">指出工作已經完成傳送 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="c269c-266">Indicates that the task finished transferring [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
|`TransferJobsTaskStartTransferringObjects`|<span data-ttu-id="c269c-267">指出工作已經開始傳送 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="c269c-267">Indicates that the task started to transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
  
###  <a name="transfer-logins-task"></a><a name="TransferLogins"></a> <span data-ttu-id="c269c-268">傳送登入工作</span><span class="sxs-lookup"><span data-stu-id="c269c-268">Transfer Logins Task</span></span>  
 <span data-ttu-id="c269c-269">下表列出「傳送登入」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-269">The following table lists the custom log entries for the Transfer Logins task.</span></span>  
  
|<span data-ttu-id="c269c-270">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-270">Log entry</span></span>|<span data-ttu-id="c269c-271">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-271">Description</span></span>|  
|---------------|-----------------|  
|`TransferLoginsTaskFinishedTransferringObjects`|<span data-ttu-id="c269c-272">指出工作已經完成傳送登入。</span><span class="sxs-lookup"><span data-stu-id="c269c-272">Indicates that the task finished transferring logins.</span></span>|  
|`TransferLoginsTaskStartTransferringObjects`|<span data-ttu-id="c269c-273">指出工作已經開始傳送登入。</span><span class="sxs-lookup"><span data-stu-id="c269c-273">Indicates that the task started to transfer logins.</span></span>|  
  
###  <a name="transfer-master-stored-procedures-task"></a><a name="TransferMasterStoredProcedures"></a> <span data-ttu-id="c269c-274">傳送主要預存程序工作</span><span class="sxs-lookup"><span data-stu-id="c269c-274">Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="c269c-275">下表列出「傳送主要預存程序」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-275">The following table lists the custom log entries for the Transfer Master Stored Procedures task.</span></span>  
  
|<span data-ttu-id="c269c-276">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-276">Log entry</span></span>|<span data-ttu-id="c269c-277">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-277">Description</span></span>|  
|---------------|-----------------|  
|`TransferStoredProceduresTaskFinishedTransferringObjects`|<span data-ttu-id="c269c-278">指出工作已經完成傳送儲存在 **master** 資料庫中的使用者定義預存程序。</span><span class="sxs-lookup"><span data-stu-id="c269c-278">Indicates that the task finished transferring user-defined stored procedures that are stored in the **master** database.</span></span>|  
|`TransferStoredProceduresTaskStartTransferringObjects`|<span data-ttu-id="c269c-279">指出工作已經開始傳送儲存在 **master** 資料庫中的使用者定義預存程序。</span><span class="sxs-lookup"><span data-stu-id="c269c-279">Indicates that the task started to transfer user-defined stored procedures that are stored in the **master** database.</span></span>|  
  
###  <a name="transfer-sql-server-objects-task"></a><a name="TransferSQLServerObjects"></a> <span data-ttu-id="c269c-280">傳送 SQL Server 物件工作</span><span class="sxs-lookup"><span data-stu-id="c269c-280">Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="c269c-281">下表列出「傳送 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-281">The following table lists the custom log entries for the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task.</span></span>  
  
|<span data-ttu-id="c269c-282">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-282">Log entry</span></span>|<span data-ttu-id="c269c-283">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-283">Description</span></span>|  
|---------------|-----------------|  
|`TransferSqlServerObjectsTaskFinishedTransferringObjects`|<span data-ttu-id="c269c-284">指出工作已經完成傳送 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="c269c-284">Indicates that the task finished transferring [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database objects.</span></span>|  
|`TransferSqlServerObjectsTaskStartTransferringObjects`|<span data-ttu-id="c269c-285">指出工作已經開始傳送 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="c269c-285">Indicates that the task started to transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database objects.</span></span>|  
  
###  <a name="web-services-task"></a><a name="WebServices"></a> <span data-ttu-id="c269c-286">Web 服務工作</span><span class="sxs-lookup"><span data-stu-id="c269c-286">Web Services Task</span></span>  
 <span data-ttu-id="c269c-287">下表列出您可以為「Web 服務」工作啟用的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-287">The following table lists the custom log entries that you can enable for the Web Services task.</span></span>  
  
|<span data-ttu-id="c269c-288">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-288">Log entry</span></span>|<span data-ttu-id="c269c-289">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-289">Description</span></span>|  
|---------------|-----------------|  
|`WSTaskBegin`|<span data-ttu-id="c269c-290">工作已經開始存取 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c269c-290">The task began to access a Web service.</span></span>|  
|`WSTaskEnd`|<span data-ttu-id="c269c-291">工作已經完成 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="c269c-291">The task completed a Web service method.</span></span>|  
|`WSTaskInfo`|<span data-ttu-id="c269c-292">關於工作的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-292">Descriptive information about the task.</span></span>|  
  
###  <a name="wmi-data-reader-task"></a><a name="WMIDataReader"></a> <span data-ttu-id="c269c-293">WMI 資料讀取器工作</span><span class="sxs-lookup"><span data-stu-id="c269c-293">WMI Data Reader Task</span></span>  
 <span data-ttu-id="c269c-294">下表列出「WMI 資料讀取器」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-294">The following table lists the custom log entries for the WMI Data Reader task.</span></span>  
  
|<span data-ttu-id="c269c-295">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-295">Log entry</span></span>|<span data-ttu-id="c269c-296">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-296">Description</span></span>|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|<span data-ttu-id="c269c-297">指出工作已經開始讀取 WMI 資料。</span><span class="sxs-lookup"><span data-stu-id="c269c-297">Indicates that the task began to read WMI data.</span></span>|  
|`WMIDataReaderOperation`|<span data-ttu-id="c269c-298">報告工作已執行的 WQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="c269c-298">Reports the WQL query that the task ran.</span></span>|  
  
###  <a name="wmi-event-watcher-task"></a><a name="WMIEventWatcher"></a> <span data-ttu-id="c269c-299">WMI 事件監看員工作</span><span class="sxs-lookup"><span data-stu-id="c269c-299">WMI Event Watcher Task</span></span>  
 <span data-ttu-id="c269c-300">下表列出「WMI 事件監看員」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-300">The following table lists the custom log entries for the WMI Event Watcher task.</span></span>  
  
|<span data-ttu-id="c269c-301">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-301">Log entry</span></span>|<span data-ttu-id="c269c-302">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-302">Description</span></span>|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|<span data-ttu-id="c269c-303">表示發生工作正在監視的事件。</span><span class="sxs-lookup"><span data-stu-id="c269c-303">Denotes that the event occurred that the task was monitoring.</span></span>|  
|`WMIEventWatcherTimedout`|<span data-ttu-id="c269c-304">指出工作已經逾時。</span><span class="sxs-lookup"><span data-stu-id="c269c-304">Indicates that the task timed out.</span></span>|  
|`WMIEventWatcherWatchingForWMIEvents`|<span data-ttu-id="c269c-305">指出工作已經開始執行 WQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="c269c-305">Indicates that the task began to execute the WQL query.</span></span> <span data-ttu-id="c269c-306">項目包含查詢。</span><span class="sxs-lookup"><span data-stu-id="c269c-306">The entry includes the query.</span></span>|  
  
###  <a name="xml-task"></a><a name="XML"></a> <span data-ttu-id="c269c-307">XML 工作</span><span class="sxs-lookup"><span data-stu-id="c269c-307">XML Task</span></span>  
 <span data-ttu-id="c269c-308">下表描述 XML 工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="c269c-308">The following table describes the custom log entry for the XML task.</span></span>  
  
|<span data-ttu-id="c269c-309">記錄項目</span><span class="sxs-lookup"><span data-stu-id="c269c-309">Log entry</span></span>|<span data-ttu-id="c269c-310">描述</span><span class="sxs-lookup"><span data-stu-id="c269c-310">Description</span></span>|  
|---------------|-----------------|  
|`XMLOperation`|<span data-ttu-id="c269c-311">提供有關工作執行之作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="c269c-311">Provides information about the operation that the task performs</span></span>|   
  
## <a name="see-also"></a><span data-ttu-id="c269c-312">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c269c-312">See Also</span></span>  
 [<span data-ttu-id="c269c-313">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="c269c-313">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
