---
title: 監視原生編譯預存程序的效能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 55548cb2-77a8-4953-8b5a-f2778a4f13cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d14d27cdc20c0f090c7a030efe05cfce4842f437
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709429"
---
# <a name="monitoring-performance-of-natively-compiled-stored-procedures"></a><span data-ttu-id="3695f-102">監視原生編譯預存程序的效能</span><span class="sxs-lookup"><span data-stu-id="3695f-102">Monitoring Performance of Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="3695f-103">本主題討論如何監視原生編譯預存程序的效能</span><span class="sxs-lookup"><span data-stu-id="3695f-103">This topic discusses how you can monitor the performance of natively compiled stored procedures</span></span>  
  
## <a name="using-extended-events"></a><span data-ttu-id="3695f-104">使用擴充的事件</span><span class="sxs-lookup"><span data-stu-id="3695f-104">Using Extended Events</span></span>  
 <span data-ttu-id="3695f-105">使用 `sp_statement_completed` 擴充事件來追蹤查詢的執行。</span><span class="sxs-lookup"><span data-stu-id="3695f-105">Use the `sp_statement_completed` extended event to trace execution of a query.</span></span> <span data-ttu-id="3695f-106">以此事件建立擴充事件工作階段，選擇性地針對特定原生編譯預存程序篩選 object_id。執行每項查詢之後都將引發此擴充事件。</span><span class="sxs-lookup"><span data-stu-id="3695f-106">Create an extended event session with this event, optionally with a filter on object_id for a particular natively compiled stored procedure, The extended event is raised after the execution of each query.</span></span> <span data-ttu-id="3695f-107">擴充事件所報告的 CPU 時間和持續時間代表了查詢的 CPU 使用率和執行時間。</span><span class="sxs-lookup"><span data-stu-id="3695f-107">The CPU time and duration reported by the extended event indicate how much CPU the query used and the execution time.</span></span> <span data-ttu-id="3695f-108">原生編譯預存程序若佔用大量的 CPU 時間，可能就會導致效能問題。</span><span class="sxs-lookup"><span data-stu-id="3695f-108">A natively compiled stored procedure that uses a lot of CPU time may have performance problems.</span></span>  
  
 <span data-ttu-id="3695f-109">`line_number` 連同擴充事件中的 `object_id` 皆可用來調查查詢。</span><span class="sxs-lookup"><span data-stu-id="3695f-109">`line_number`, along with the `object_id` in the extended event can be used to investigate the query.</span></span> <span data-ttu-id="3695f-110">使用下列查詢即可擷取程序定義。</span><span class="sxs-lookup"><span data-stu-id="3695f-110">The following query can be used to retrieve the procedure definition.</span></span> <span data-ttu-id="3695f-111">行號可用來識別定義內的查詢：</span><span class="sxs-lookup"><span data-stu-id="3695f-111">The line number can be used to identify the query within the definition:</span></span>  
  
```sql  
select [definition] from sys.sql_modules where object_id=object_id  
```  
  
 <span data-ttu-id="3695f-112">如需有關擴充事件的詳細資訊 `sp_statement_completed` ，請參閱[如何取出造成事件的語句](https://blogs.msdn.com/b/extended_events/archive/2010/05/07/making-a-statement-how-to-retrieve-the-t-sql-statement-that-caused-an-event.aspx)。</span><span class="sxs-lookup"><span data-stu-id="3695f-112">For more information about the `sp_statement_completed` extended event, see [How to retrieve the statement that caused an event](https://blogs.msdn.com/b/extended_events/archive/2010/05/07/making-a-statement-how-to-retrieve-the-t-sql-statement-that-caused-an-event.aspx).</span></span>  
  
## <a name="using-data-management-views"></a><span data-ttu-id="3695f-113">使用資料管理檢視</span><span class="sxs-lookup"><span data-stu-id="3695f-113">Using Data Management Views</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3695f-114">支援收集原生編譯預存程序在程序層級和查詢層級的執行統計資料。</span><span class="sxs-lookup"><span data-stu-id="3695f-114">supports collecting execution statistics for natively compiled stored procedures, both on the procedure level and the query level.</span></span> <span data-ttu-id="3695f-115">收集執行統計資料會影響效能，所以預設並未啟用。</span><span class="sxs-lookup"><span data-stu-id="3695f-115">Collecting execution statistics is not enabled by default due to performance impact.</span></span>  
  
 <span data-ttu-id="3695f-116">您可以使用 [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql) 啟用和停用原生編譯預存程序的統計資料收集。</span><span class="sxs-lookup"><span data-stu-id="3695f-116">You can enable and disable statistics collection on natively compiled stored procedures using [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="3695f-117">使用 [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql) 啟用統計資料收集時，您可以使用 [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) 監視原生編譯預存程序的效能。</span><span class="sxs-lookup"><span data-stu-id="3695f-117">When statistics collection is enabled with [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql), you can use [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) to monitor performance of a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="3695f-118">使用 [sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql) 啟用統計資料收集時，您可以使用 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) 監視原生編譯預存程序的效能。</span><span class="sxs-lookup"><span data-stu-id="3695f-118">When statistics collection is enabled with [sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql), you can use [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) to monitor performance of a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="3695f-119">在一開始收集時，啟用統計資料集合。</span><span class="sxs-lookup"><span data-stu-id="3695f-119">At the start of collection, enable statistics collection.</span></span> <span data-ttu-id="3695f-120">接著，執行原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="3695f-120">Then, execute the natively compiled stored procedure.</span></span> <span data-ttu-id="3695f-121">在結束收集後，停用統計資料集合。</span><span class="sxs-lookup"><span data-stu-id="3695f-121">At the end of collection, disable statistics collection.</span></span> <span data-ttu-id="3695f-122">接著，分析 DMV 所傳回的執行統計資料。</span><span class="sxs-lookup"><span data-stu-id="3695f-122">Then, analyze the execution statistics returned by the DMVs.</span></span>  
  
 <span data-ttu-id="3695f-123">收集統計資料之後，使用 [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) 和 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) 分別可查詢原生編譯預存程序的程序層級和查詢層級執行統計資料。</span><span class="sxs-lookup"><span data-stu-id="3695f-123">After you collect statistics, the execution statistics for natively compiled stored procedures can be queried for a procedure with [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql), and for queries with [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3695f-124">如果統計資料集合啟用的對象是原生編譯預存程序，則收集的工作者時間單位為毫秒。</span><span class="sxs-lookup"><span data-stu-id="3695f-124">For natively compiled stored procedures when statistics collection is enabled, worker time is collected in milliseconds.</span></span> <span data-ttu-id="3695f-125">若查詢的執行時間少於一毫秒，其值將會是 0。</span><span class="sxs-lookup"><span data-stu-id="3695f-125">If the query executes in less than a millisecond, the value will be 0.</span></span> <span data-ttu-id="3695f-126">如果原生編譯預存程序執行數次的時間都少於 1 毫秒， **total_worker_time** 可能就不準確。</span><span class="sxs-lookup"><span data-stu-id="3695f-126">For natively compiled stored procedures, **total_worker_time** may not be accurate if many executions take less than 1 millisecond.</span></span>  
  
 <span data-ttu-id="3695f-127">下列查詢會在收集統計資料之後傳回目前資料庫中原生編譯預存程序的程序名稱和執行統計資料：</span><span class="sxs-lookup"><span data-stu-id="3695f-127">The following query returns the procedure names and execution statistics for natively compiled stored procedures in the current database, after statistics collection:</span></span>  
  
```sql  
select object_id,  
       object_name(object_id) as 'object name',  
       cached_time,  
       last_execution_time,  
       execution_count,  
       total_worker_time,  
       last_worker_time,  
       min_worker_time,  
       max_worker_time,  
       total_elapsed_time,  
       last_elapsed_time,  
       min_elapsed_time,  
       max_elapsed_time   
from sys.dm_exec_procedure_stats  
where database_id=db_id() and object_id in (select object_id   
from sys.sql_modules where uses_native_compilation=1)  
order by total_worker_time desc  
```  
  
 <span data-ttu-id="3695f-128">下列查詢會傳回目前資料庫中已收集統計資料的原生編譯預存程序內，所有查詢的查詢文字和執行統計資料，依工作者時間總計以遞減順序排序：</span><span class="sxs-lookup"><span data-stu-id="3695f-128">The following query returns the query text as well as execution statistics for all queries in natively compiled stored procedures in the current database for which statistics have been collected, ordered by total worker time, in descending order:</span></span>  
  
```sql  
select st.objectid,   
       object_name(st.objectid) as 'object name',   
       SUBSTRING(st.text, (qs.statement_start_offset/2) + 1, ((qs.statement_end_offset-qs.statement_start_offset)/2) + 1) as 'query text',   
       qs.creation_time,  
       qs.last_execution_time,  
       qs.execution_count,  
       qs.total_worker_time,  
       qs.last_worker_time,  
       qs.min_worker_time,  
       qs.max_worker_time,  
       qs.total_elapsed_time,  
       qs.last_elapsed_time,  
       qs.min_elapsed_time,  
       qs.max_elapsed_time  
from sys.dm_exec_query_stats qs cross apply sys.dm_exec_sql_text(sql_handle) st  
where  st.dbid=db_id() and st.objectid in (select object_id   
from sys.sql_modules where uses_native_compilation=1)  
order by qs.total_worker_time desc  
```  
  
 <span data-ttu-id="3695f-129">原生編譯預存程序支援 SHOWPLAN_XML (估計執行計畫)。</span><span class="sxs-lookup"><span data-stu-id="3695f-129">Natively compiled stored procedures support SHOWPLAN_XML (estimated execution plan).</span></span> <span data-ttu-id="3695f-130">估計執行計畫可用來檢查查詢計劃，以找出任何的計劃錯誤問題。</span><span class="sxs-lookup"><span data-stu-id="3695f-130">The estimated execution plan can be used to inspect the query plan, to find any bad plan issues.</span></span> <span data-ttu-id="3695f-131">計劃錯誤的常見原因包括：</span><span class="sxs-lookup"><span data-stu-id="3695f-131">Common reasons for bad plans are:</span></span>  
  
-   <span data-ttu-id="3695f-132">在建立程序之前未先更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="3695f-132">Stats were not updated before the procedure was created.</span></span>  
  
-   <span data-ttu-id="3695f-133">遺漏索引。</span><span class="sxs-lookup"><span data-stu-id="3695f-133">Missing indexes</span></span>  
  
 <span data-ttu-id="3695f-134">執行程序表 XML 可透過執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)]取得：</span><span class="sxs-lookup"><span data-stu-id="3695f-134">Showplan XML is obtained by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
```sql  
SET SHOWPLAN_XML ON  
GO  
EXEC my_proc   
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 <span data-ttu-id="3695f-135">或者，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中選取程序名稱，然後按一下 **[顯示估計執行計畫]** 。</span><span class="sxs-lookup"><span data-stu-id="3695f-135">Alternatively, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the procedure name and click **Display Estimated Execution Plan**.</span></span>  
  
 <span data-ttu-id="3695f-136">原生編譯預存程序的估計執行計畫會顯示程序內各查詢的查詢運算子和運算式。</span><span class="sxs-lookup"><span data-stu-id="3695f-136">The estimated execution plan for natively compiled stored procedures shows the query operators and expressions for the queries in the procedure.</span></span> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="3695f-137">並未支援原生編譯預存程序的所有 SHOWPLAN_XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="3695f-137">does not support all SHOWPLAN_XML attributes for natively compiled stored procedures.</span></span> <span data-ttu-id="3695f-138">例如，與查詢最佳化工具成本相關的屬性並未納入程序的 SHOWPLAN_XML。</span><span class="sxs-lookup"><span data-stu-id="3695f-138">For example, attributes related to query optimizer costing are not part of the SHOWPLAN_XML for the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3695f-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3695f-139">See Also</span></span>  
 [<span data-ttu-id="3695f-140">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="3695f-140">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
