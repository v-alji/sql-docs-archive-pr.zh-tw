---
title: 使用 SQL Server Profiler 檢視和分析追蹤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], viewing traces
- SQL Server Profiler, viewing traces
- traces [SQL Server], viewing
- SQL Server Profiler, troubleshooting
- troubleshooting [SQL Server], traces
- events [SQL Server], finding inside trace
- Profiler [SQL Server Profiler], troubleshooting
- traces [SQL Server], events
ms.assetid: 17e821ca-a12e-4192-acc1-96765d9ae266
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3e848fe9a07d838631eef1737c2a7679b67e649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593727"
---
# <a name="view-and-analyze-traces-with-sql-server-profiler"></a><span data-ttu-id="bdaec-102">使用 SQL Server Profiler 檢視和分析追蹤</span><span class="sxs-lookup"><span data-stu-id="bdaec-102">View and Analyze Traces with SQL Server Profiler</span></span>
  <span data-ttu-id="bdaec-103">可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來檢視追蹤中擷取的事件資料。</span><span class="sxs-lookup"><span data-stu-id="bdaec-103">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to view captured event data in a trace.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="bdaec-104">會根據定義的追蹤屬性來顯示資料。</span><span class="sxs-lookup"><span data-stu-id="bdaec-104">displays data based on defined trace properties.</span></span> <span data-ttu-id="bdaec-105">分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料的方法之一，是將資料複製到另一個程式，例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="bdaec-105">One way to analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data is to copy the data to another program, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor.</span></span> [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="bdaec-106">如果追蹤內包含 **Text** 資料行，則 Tuning Advisor 可以使用包含了 SQL 批次和遠端程序呼叫 (RPC) 事件的追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="bdaec-106">Tuning Advisor can use a trace file that contains SQL batch and remote procedure call (RPC) events if the **Text** data column is included in the trace.</span></span> <span data-ttu-id="bdaec-107">為了確保能擷取正確的事件和資料行，以便用於 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor，請使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]隨附的預先定義「微調」範本。</span><span class="sxs-lookup"><span data-stu-id="bdaec-107">To make sure that the correct events and columns are captured for use with [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, use the predefined Tuning template that is supplied with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="bdaec-108">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]開啟追蹤時，如果檔案是由 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或「SQL 追蹤」系統預存程序建立，則追蹤檔案的副檔名不需要是 .trc。</span><span class="sxs-lookup"><span data-stu-id="bdaec-108">When you open a trace by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the trace file does not need to have the .trc file extension if the file was created by either [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or SQL Trace system stored procedures.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="bdaec-109">也可以讀取「SQL 追蹤」的 .log 檔案與泛用的 SQL 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="bdaec-109">can also read SQL Trace .log files and generic SQL script files.</span></span> <span data-ttu-id="bdaec-110">開啟副檔名不是 .log 的「SQL 追蹤」 .log 檔 (例如 trace.txt) 時，請將檔案格式指定成 **SQLTrace_Log** 。</span><span class="sxs-lookup"><span data-stu-id="bdaec-110">When opening a SQL Trace .log file that does not have a .log file extension, such as trace.txt, specify **SQLTrace_Log** as the file format.</span></span>  
  
 <span data-ttu-id="bdaec-111">您可以設定 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 日期和時間的顯示格式，以協助追蹤分析。</span><span class="sxs-lookup"><span data-stu-id="bdaec-111">You can configure the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] date and time display format to assist in trace analysis.</span></span>  
  
## <a name="troubleshooting-data"></a><span data-ttu-id="bdaec-112">疑難排解資料</span><span class="sxs-lookup"><span data-stu-id="bdaec-112">Troubleshooting Data</span></span>  
 <span data-ttu-id="bdaec-113">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，您可以使用 **Duration**、 **CPU**、 **Reads**或 **Writes** 資料行來分組追蹤或追蹤檔案，以針對資料進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="bdaec-113">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can troubleshoot data by grouping traces or trace files by the **Duration**, **CPU**, **Reads**, or **Writes** data columns.</span></span> <span data-ttu-id="bdaec-114">例如，執行效率差或邏輯讀取作業數過高的查詢，可能需要進行資料的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="bdaec-114">Examples of data you might troubleshoot are queries that perform poorly or that have exceptionally high numbers of logical read operations.</span></span>  
  
 <span data-ttu-id="bdaec-115">可透過將追蹤儲存到資料表，並使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 來查詢事件資料而找出額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="bdaec-115">Additional information can be found by saving traces to tables and using [!INCLUDE[tsql](../../includes/tsql-md.md)] to query the event data.</span></span> <span data-ttu-id="bdaec-116">例如，若要判斷有哪些 **SQL:BatchCompleted** 事件的等候時間過量，請執行以下陳述式：</span><span class="sxs-lookup"><span data-stu-id="bdaec-116">For example, to determine which **SQL:BatchCompleted** events had excessive wait time, execute the following:</span></span>  
  
```  
SELECT  TextData, Duration, CPU  
FROM    trace_table_name  
WHERE   EventClass = 12 -- SQL:BatchCompleted events  
AND     CPU < (Duration * 1000)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="bdaec-117">伺服器會以百萬分之一秒為單位 (百萬分之一秒，或 10<sup>-6</sup>秒) 報告事件的持續時間，並以毫秒為單位 (千分之一秒，或 10<sup>-3</sup>秒) 報告事件使用的 CPU 時間量。</span><span class="sxs-lookup"><span data-stu-id="bdaec-117">The server reports the duration of an event in microseconds (one millionth, or 10<sup>-6</sup>, of a second) and the amount of CPU time used by the event in milliseconds (one thousandth, or 10<sup>-3</sup>, of a second).</span></span> <span data-ttu-id="bdaec-118">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 圖形化使用者介面預設會以毫秒為單位來顯示 **Duration** 資料行，但是當追蹤儲存到檔案或資料庫資料表時，會以百萬分之一秒為單位來寫入 **Duration** 資料行值。</span><span class="sxs-lookup"><span data-stu-id="bdaec-118">The [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] graphical user interface displays the **Duration** column in milliseconds by default, but when a trace is saved to either a file or a database table, the **Duration** column value is written in microseconds.</span></span>  
  
## <a name="displaying-object-names-when-viewing-traces"></a><span data-ttu-id="bdaec-119">檢視追蹤時顯示物件名稱</span><span class="sxs-lookup"><span data-stu-id="bdaec-119">Displaying Object Names When Viewing Traces</span></span>  
 <span data-ttu-id="bdaec-120">如果想要顯示物件名稱而非物件識別碼 (**Object ID**)，則必須同時擷取 **Server Name** 、 **Database ID** 與 **Object Name** 資料行。</span><span class="sxs-lookup"><span data-stu-id="bdaec-120">If you wish to display the name of an object rather than the object identifier (**Object ID**), you must capture the **Server Name** and **Database ID** data columns along with the **Object Name** data column.</span></span>  
  
 <span data-ttu-id="bdaec-121">如果選擇要以 **Object ID** 資料行分組，請一定要先將 **Server Name** 與 **Database ID** 資料行分組，再以 **Object ID** 資料行來分組。</span><span class="sxs-lookup"><span data-stu-id="bdaec-121">If you choose to group by the **Object ID** data column, make sure you group by the **Server Name** and **Database ID** data columns first, and then by the **Object ID** data column.</span></span> <span data-ttu-id="bdaec-122">同樣地，如果選擇要以 **Index ID** 資料行分組，請一定要先將 **Server Name**、 **Database ID**與 **Object ID** 資料行分組，再以 **Index ID** 資料行來分組。</span><span class="sxs-lookup"><span data-stu-id="bdaec-122">Similarly, if you choose to group by the **Index ID** data column, make sure you group by the **Server Name**, **Database ID**, and **Object ID** data columns first, and then by the **Index ID** data columns.</span></span> <span data-ttu-id="bdaec-123">您必須採用這種分組順序，因為物件識別碼與索引識別碼在伺服器與資料庫 (以及在索引識別碼的物件) 之間並不是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bdaec-123">You must group in this order because object and index IDs are not unique among servers and databases (and among objects for index IDs).</span></span>  
  
## <a name="finding-specific-events-within-a-trace"></a><span data-ttu-id="bdaec-124">在追蹤中找出特定事件</span><span class="sxs-lookup"><span data-stu-id="bdaec-124">Finding Specific Events Within a Trace</span></span>  
 <span data-ttu-id="bdaec-125">若要在追蹤中尋找和分組事件，請遵循這些步驟：</span><span class="sxs-lookup"><span data-stu-id="bdaec-125">To find and group events in a trace, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bdaec-126">建立您的追蹤。</span><span class="sxs-lookup"><span data-stu-id="bdaec-126">Create your trace.</span></span>  
  
    -   <span data-ttu-id="bdaec-127">定義追蹤時，請擷取 **Event Class**、 **ClientProcessID**與 **Start Time** 資料行，以及您想要擷取的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="bdaec-127">When defining the trace, capture the **Event Class**, **ClientProcessID**, and **Start Time** data columns in addition to any other data columns you want to capture.</span></span> <span data-ttu-id="bdaec-128">如需詳細資訊，請參閱[建立追蹤 &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="bdaec-128">For more information, see [Create a Trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="bdaec-129">依照 **Event Class**資料行來將擷取的資料分組，並將追蹤擷取到檔案或資料表中。</span><span class="sxs-lookup"><span data-stu-id="bdaec-129">Group the captured data by the **Event Class**data column, and capture the trace to a file or table.</span></span> <span data-ttu-id="bdaec-130">若要將擷取的資料分組，請在 [追蹤屬性] 對話方塊的 [事件選取範圍] 索引標籤上，按一下 [組織資料行]。</span><span class="sxs-lookup"><span data-stu-id="bdaec-130">To group the captured data, click **Organize Columns** on the **Events Selection** tab of the Trace Properties dialog box.</span></span> <span data-ttu-id="bdaec-131">如需詳細資訊，請參閱[組織追蹤內顯示的資料行 &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="bdaec-131">For more information, see [Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="bdaec-132">啟動追蹤，並在超過指定的時間或所擷取的事件數已達上限後停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="bdaec-132">Start the trace and stop it after the appropriate time has passed or number of events have been captured.</span></span>  
  
2.  <span data-ttu-id="bdaec-133">找出目標事件。</span><span class="sxs-lookup"><span data-stu-id="bdaec-133">Find the target events.</span></span>  
  
    -   <span data-ttu-id="bdaec-134">開啟追蹤檔案或資料表，然後展開想要的事件類別節點；例如， **Deadlock Chain**。</span><span class="sxs-lookup"><span data-stu-id="bdaec-134">Open the trace file or table, and expand the node of the desired event class; for example, **Deadlock Chain**.</span></span> <span data-ttu-id="bdaec-135">如需詳細資訊，請參閱 [開啟追蹤檔案 &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 或 [開啟追蹤資料表 &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)隨附的預先定義「微調」範本。</span><span class="sxs-lookup"><span data-stu-id="bdaec-135">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="bdaec-136">搜尋整個追蹤資料直到您找到要查看的事件為止 (請使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 之 [編輯] 功能表上的 [尋找] 命令來協助您在追蹤中尋找值)。</span><span class="sxs-lookup"><span data-stu-id="bdaec-136">Search through the trace data until you find the events for which you are looking (use the **Find** command on the **Edit** menu of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to help you find values in the trace).</span></span> <span data-ttu-id="bdaec-137">請注意位於追蹤事件之 **ClientProcessID** 與 **Start Time** 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="bdaec-137">Note the values in the **ClientProcessID** and **Start Time** data columns of the events you trace.</span></span>  
  
3.  <span data-ttu-id="bdaec-138">在內容中顯示事件。</span><span class="sxs-lookup"><span data-stu-id="bdaec-138">Display the events in context.</span></span>  
  
    -   <span data-ttu-id="bdaec-139">顯示追蹤屬性，並以 **ClientProcessID**資料行分組，而非以 **Event Class** 資料行。</span><span class="sxs-lookup"><span data-stu-id="bdaec-139">Display the trace properties, and group by the **ClientProcessID**data column rather than by the **Event Class** data column.</span></span>  
  
    -   <span data-ttu-id="bdaec-140">將您要檢視的每一個用戶端處理序識別碼節點展開。</span><span class="sxs-lookup"><span data-stu-id="bdaec-140">Expand the nodes of each client process ID you want to view.</span></span> <span data-ttu-id="bdaec-141">手動搜尋整個追蹤，或使用 [尋找]  直到您找出先前標註為目標事件之 [開始時間]  的值為止。</span><span class="sxs-lookup"><span data-stu-id="bdaec-141">Search through the trace manually, or use **Find** until you find the previously noted **Start Time**values of the target events.</span></span> <span data-ttu-id="bdaec-142">這些事件與屬於每一個選取之用戶端程序識別碼的其他事件，會依時間先後順序顯示出來。</span><span class="sxs-lookup"><span data-stu-id="bdaec-142">The events are displayed in chronological order with the other events that belong to each selected client process ID.</span></span> <span data-ttu-id="bdaec-143">例如，在追蹤內擷取的 **Deadlock** 和 **Deadlock Chain**事件，會緊接在所展開之用戶端處理序識別碼內的 **SQL:BatchStarting**事件後面出現。</span><span class="sxs-lookup"><span data-stu-id="bdaec-143">For example, the **Deadlock** and **Deadlock Chain**events, captured within the trace, appear immediately after the **SQL:BatchStarting**events within the expanded client process ID.</span></span>  
  
 <span data-ttu-id="bdaec-144">要尋找任何已分組的事件可以使用相同的技術。</span><span class="sxs-lookup"><span data-stu-id="bdaec-144">The same technique can be used to find any grouped events.</span></span> <span data-ttu-id="bdaec-145">您找到要搜尋的事件之後，請依 **ClientProcessID**、 **ApplicationName**或是另一個事件類別來分組，以便按照事件的發生先後順序來檢視相關的活動。</span><span class="sxs-lookup"><span data-stu-id="bdaec-145">Once you have found the events you seek, group them by **ClientProcessID**, **ApplicationName**, or another event class to view related activity in chronological order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdaec-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdaec-146">See Also</span></span>  
 <span data-ttu-id="bdaec-147">[檢視已儲存的追蹤 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="bdaec-147">[View a Saved Trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md) </span></span>  
 <span data-ttu-id="bdaec-148">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdaec-148">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span></span>  
 <span data-ttu-id="bdaec-149">[檢視篩選資訊 &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bdaec-149">[View Filter Information &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="bdaec-150">[檢視篩選資訊 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="bdaec-150">[View Filter Information &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md) </span></span>  
 <span data-ttu-id="bdaec-151">[開啟追蹤檔案 &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bdaec-151">[Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="bdaec-152">開啟追蹤資料表 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="bdaec-152">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](open-a-trace-table-sql-server-profiler.md)  
  
  
