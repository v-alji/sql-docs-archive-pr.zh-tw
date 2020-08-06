---
title: 將現有的 SQL 追蹤指令碼轉換為擴充事件工作階段 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, convert script to extended events
- extended events [SQL Server], convert SQL Trace script
ms.assetid: 4c8f29e6-0a37-490f-88b3-33493871b3f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e5b0d0e20fbf4fd55398c130abf6cfff128ebe8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598404"
---
# <a name="convert-an-existing-sql-trace-script-to-an-extended-events-session"></a><span data-ttu-id="3eddb-102">將現有的 SQL 追蹤指令碼轉換為擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="3eddb-102">Convert an Existing SQL Trace Script to an Extended Events Session</span></span>
  <span data-ttu-id="3eddb-103">如果您有現有的 SQL 追蹤指令碼想要轉換成「擴充事件」工作階段，您可以使用本主題的程序建立同等的「擴充事件」工作階段。</span><span class="sxs-lookup"><span data-stu-id="3eddb-103">If you have an existing SQL Trace script that you want to convert to an Extended Events session, you can use the procedures in this topic to create an equivalent Extended Events session.</span></span> <span data-ttu-id="3eddb-104">您可以藉由使用 trace_xe_action_map 和 trace_xe_event_map 系統資料表中的資訊來收集執行轉換所必須擁有的資訊。</span><span class="sxs-lookup"><span data-stu-id="3eddb-104">By using the information in the trace_xe_action_map and trace_xe_event_map system tables, you can collect the information that you must have to do the conversion.</span></span>  
  
 <span data-ttu-id="3eddb-105">這些步驟包含以下內容：</span><span class="sxs-lookup"><span data-stu-id="3eddb-105">The steps include the following:</span></span>  
  
1.  <span data-ttu-id="3eddb-106">執行現有的指令碼來建立 SQL 追蹤工作階段，然後取得追蹤的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3eddb-106">Execute the existing script to create a SQL Trace session, and then obtain the ID of the trace.</span></span>  
  
2.  <span data-ttu-id="3eddb-107">執行使用 fn_trace_geteventinfo 函數的查詢，以便在同等的「擴充事件」事件和動作中，找出每一個「SQL 追蹤」事件類別以及其關聯的資料行。</span><span class="sxs-lookup"><span data-stu-id="3eddb-107">Run a query that uses the fn_trace_geteventinfo function to find the equivalent Extended Events events and actions for each SQL Trace event class and its associated columns.</span></span>  
  
3.  <span data-ttu-id="3eddb-108">使用 fn_trace_getfilterinfo 函數可列出要使用的篩選以及同等的「擴充事件」動作。</span><span class="sxs-lookup"><span data-stu-id="3eddb-108">Use the fn_trace_getfilterinfo function to list the filters and the equivalent Extended Events actions to use.</span></span>  
  
4.  <span data-ttu-id="3eddb-109">使用同等的「擴充事件」事件、動作和述詞 (篩選器) 手動建立「擴充事件」工作階段。</span><span class="sxs-lookup"><span data-stu-id="3eddb-109">Manually create an Extended Events session, using the equivalent Extended Events events, actions, and predicates (filters).</span></span>  
  
## <a name="to-obtain-the-trace-id"></a><span data-ttu-id="3eddb-110">若要取得追蹤識別碼</span><span class="sxs-lookup"><span data-stu-id="3eddb-110">To obtain the trace ID</span></span>  
  
1.  <span data-ttu-id="3eddb-111">在查詢編輯器中開啟 SQL 追蹤指令碼，並執行此指令碼來建立追蹤工作階段。</span><span class="sxs-lookup"><span data-stu-id="3eddb-111">Open the SQL Trace script in Query Editor, and then execute the script to create the trace session.</span></span> <span data-ttu-id="3eddb-112">請注意，不需要執行追蹤工作階段也可完成此程序。</span><span class="sxs-lookup"><span data-stu-id="3eddb-112">Note that the trace session does not need to be running to complete this procedure.</span></span>  
  
2.  <span data-ttu-id="3eddb-113">取得追蹤的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3eddb-113">Obtain the ID of the trace.</span></span> <span data-ttu-id="3eddb-114">若要這樣做，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="3eddb-114">To do this, use the following query:</span></span>  
  
    ```sql
    SELECT * FROM sys.traces;  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="3eddb-115">追蹤識別碼 1 通常表示預設追蹤。</span><span class="sxs-lookup"><span data-stu-id="3eddb-115">Trace ID 1 typically indicates the default trace.</span></span>  
  
## <a name="to-determine-the-extended-events-equivalents"></a><span data-ttu-id="3eddb-116">若要判斷擴充事件同等項目</span><span class="sxs-lookup"><span data-stu-id="3eddb-116">To determine the Extended Events equivalents</span></span>  
  
1.  <span data-ttu-id="3eddb-117">若要判斷同等的「擴充事件」事件和動作，請執行下列查詢，其中 *trace_id* 設定為您在上一個程序中取得之追蹤識別碼的值。</span><span class="sxs-lookup"><span data-stu-id="3eddb-117">To determine the equivalent Extended Events events and actions, run the following query, where *trace_id* is set to the value of the trace ID that you obtained in the previous procedure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3eddb-118">在這個範例中，將會使用預設追蹤的追蹤識別碼 (1)。</span><span class="sxs-lookup"><span data-stu-id="3eddb-118">In this example, the trace ID for the default trace (1) is used.</span></span>  
  
    ```sql
    USE MASTER;  
    GO  
    DECLARE @trace_id int;  
    SET @trace_id = 1;  
    SELECT DISTINCT el.eventid, em.package_name, em.xe_event_name AS 'event'  
       , el.columnid, ec.xe_action_name AS 'action'  
    FROM (sys.fn_trace_geteventinfo(@trace_id) AS el  
       LEFT OUTER JOIN sys.trace_xe_event_map AS em  
          ON el.eventid = em.trace_event_id)  
    LEFT OUTER JOIN sys.trace_xe_action_map AS ec  
       ON el.columnid = ec.trace_column_id  
    WHERE em.xe_event_name IS NOT NULL AND ec.xe_action_name IS NOT NULL;  
    ```  
  
     <span data-ttu-id="3eddb-119">將會傳回同等的「擴充事件」事件識別碼、封裝名稱、事件名稱、資料行識別碼和動作名稱。</span><span class="sxs-lookup"><span data-stu-id="3eddb-119">The equivalent Extended Events event ID, package name, event name, column ID and action name are returned.</span></span> <span data-ttu-id="3eddb-120">您將會在本主題稍後的＜若要建立擴充事件工作階段＞程序中使用這個輸出。</span><span class="sxs-lookup"><span data-stu-id="3eddb-120">You will use this output in the procedure "To create the Extended Events session" later in this topic.</span></span>  
  
     <span data-ttu-id="3eddb-121">在某些情況下，篩選的資料行會對應到事件資料欄位，預設會將此欄位併入「擴充事件」事件內。</span><span class="sxs-lookup"><span data-stu-id="3eddb-121">In some cases, the filtered column maps to an event data field that is included by default in the Extended Events event.</span></span> <span data-ttu-id="3eddb-122">因此，"Extended_Events_action_name" 資料行將會是 NULL。</span><span class="sxs-lookup"><span data-stu-id="3eddb-122">Therefore, the "Extended_Events_action_name" column will be NULL.</span></span> <span data-ttu-id="3eddb-123">如果發生這種情況，您必須執行下列動作，以判斷哪一個資料欄位相當於篩選的資料行：</span><span class="sxs-lookup"><span data-stu-id="3eddb-123">If this occurs, you must do the following to determine which data field is equivalent to the filtered column:</span></span>  
  
    1.  <span data-ttu-id="3eddb-124">如果是傳回 NULL 的動作，請識別指令碼中有哪一個 SQL 追蹤事件類別包含正在篩選的資料行。</span><span class="sxs-lookup"><span data-stu-id="3eddb-124">For the actions that return NULL, identify which SQL Trace event classes in the script contain the column that is being filtered.</span></span>  
  
         <span data-ttu-id="3eddb-125">例如，您可能已經使用 SP:StmtCompleted 事件類別，並在 Duration 追蹤資料行名稱 (SQL 追蹤事件類別識別碼 45 和 SQL 追蹤資料行識別碼 13) 上指定篩選。</span><span class="sxs-lookup"><span data-stu-id="3eddb-125">For example, you may have used the SP:StmtCompleted event class, and specified a filter on the Duration trace column name (SQL Trace event class ID 45, and SQL Trace column ID 13).</span></span> <span data-ttu-id="3eddb-126">在此情況下，動作名稱會以 NULL 形式出現在查詢結果中。</span><span class="sxs-lookup"><span data-stu-id="3eddb-126">In this case, the action name will appear as NULL in the query results.</span></span>  
  
    2.  <span data-ttu-id="3eddb-127">針對您在上一個步驟所識別的每個 SQL 追蹤事件類別，尋找同等的「擴充事件」事件名稱</span><span class="sxs-lookup"><span data-stu-id="3eddb-127">For each SQL Trace event class that you identified in the previous step, find the equivalent Extended Events event name.</span></span> <span data-ttu-id="3eddb-128">(如果您不確定同等的事件名稱，請使用 [檢視同等於 SQL 追蹤事件類別的擴充事件項目](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)主題中的查詢)。</span><span class="sxs-lookup"><span data-stu-id="3eddb-128">(If you are not sure of the equivalent event name, use the query in the topic [View the Extended Events Equivalents to SQL Trace Event Classes](view-the-extended-events-equivalents-to-sql-trace-event-classes.md).)</span></span>  
  
    3.  <span data-ttu-id="3eddb-129">使用下列查詢來識別正確的資料欄位，這些欄位用於您在上一個步驟所識別的事件。</span><span class="sxs-lookup"><span data-stu-id="3eddb-129">Use the following query to identify the correct data fields to use for the events that you identified in the previous step.</span></span> <span data-ttu-id="3eddb-130">此查詢會在 "event_field" 資料行中顯示「擴充事件」資料欄位。</span><span class="sxs-lookup"><span data-stu-id="3eddb-130">The query shows the Extended Events data fields in the "event_field" column.</span></span> <span data-ttu-id="3eddb-131">在此查詢中，使用您在上一個步驟所指定的事件名稱來取代 <事件名稱>\*\*。</span><span class="sxs-lookup"><span data-stu-id="3eddb-131">In the query, replace *<event_name>* with the name of an event that you specified in the previous step.</span></span>  
  
        ```sql
        SELECT xp.name package_name, xe.name event_name  
           ,xc.name event_field, xc.description  
        FROM sys.trace_xe_event_map AS em  
        INNER JOIN sys.dm_xe_objects AS xe  
           ON em.xe_event_name = xe.name  
        INNER JOIN sys.dm_xe_packages AS xp  
           ON xe.package_guid = xp.guid AND em.package_name = xp.name  
        INNER JOIN sys.dm_xe_object_columns AS xc  
           ON xe.name = xc.object_name  
        WHERE xe.object_type = 'event' AND xc.column_type <> 'readonly'  
           AND em.xe_event_name = '<event_name>';  
        ```  
  
         <span data-ttu-id="3eddb-132">例如，SP:StmtCompleted 事件類別會對應到 sp_statement_completed「擴充事件」事件。</span><span class="sxs-lookup"><span data-stu-id="3eddb-132">For example, the SP:StmtCompleted event class maps to the sp_statement_completed Extended Events event.</span></span> <span data-ttu-id="3eddb-133">如果您指定 sp_statement_completed 當作查詢中的事件名稱，則 "event_field" 資料行會顯示預設隨附在事件中的欄位。</span><span class="sxs-lookup"><span data-stu-id="3eddb-133">If you specify sp_statement_completed as the event name in the query, the "event_field" column shows the fields that are included by default with the event.</span></span> <span data-ttu-id="3eddb-134">查看欄位時，可以看到「持續時間」欄位。</span><span class="sxs-lookup"><span data-stu-id="3eddb-134">Looking at the fields, you can see that there is a "duration" field.</span></span> <span data-ttu-id="3eddb-135">若要在同等的「擴充事件」工作階段中建立篩選器，您可加入類似 "WHERE duration > 0" 的述詞。</span><span class="sxs-lookup"><span data-stu-id="3eddb-135">To create the filter in the equivalent Extended Events session, you would add a predicate such as "WHERE duration > 0".</span></span> <span data-ttu-id="3eddb-136">如需範例，請參閱本主題的＜若要建立擴充事件工作階段＞程序。</span><span class="sxs-lookup"><span data-stu-id="3eddb-136">For an example, see the "To create the Extended Events session" procedure in this topic.</span></span>  
  
## <a name="to-create-the-extended-events-session"></a><span data-ttu-id="3eddb-137">若要建立擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="3eddb-137">To create the Extended Events session</span></span>  
 <span data-ttu-id="3eddb-138">使用查詢編輯器建立「擴充事件」工作階段，並將輸出寫入檔案目標。</span><span class="sxs-lookup"><span data-stu-id="3eddb-138">Use Query Editor to create the Extended Events session, and to write the output to a file target.</span></span> <span data-ttu-id="3eddb-139">下列步驟說明單一查詢，連同示範如何建立查詢的說明。</span><span class="sxs-lookup"><span data-stu-id="3eddb-139">The following steps describe a single query, with explanations to show you how to build the query.</span></span> <span data-ttu-id="3eddb-140">如需完整查詢範例，請參閱本主題的＜範例＞一節。</span><span class="sxs-lookup"><span data-stu-id="3eddb-140">For the full query example, see the "Example" section of this topic.</span></span>  
  
1.  <span data-ttu-id="3eddb-141">加入陳述式來建立事件工作階段，使用您想要用於「擴充事件」工作階段的名稱來取代*session_name* 。</span><span class="sxs-lookup"><span data-stu-id="3eddb-141">Add statements to create the event session, replacing s*ession_name* with the name that you want to use for the Extended Events session.</span></span>  
  
    ```sql
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
       DROP EVENT SESSION [Session_Name] ON SERVER;  
    CREATE EVENT SESSION [Session_Name]  
    ON SERVER;  
    ```  
  
2.  <span data-ttu-id="3eddb-142">加入在＜若要判斷擴充事件同等項目＞程序中當做輸出傳回的「擴充事件」事件和動作，並加入您在＜若要判斷指令碼中所使用的篩選器＞程序中所識別的述詞 (篩選器)。</span><span class="sxs-lookup"><span data-stu-id="3eddb-142">Add the Extended Events events and actions that were returned as output in the procedure "Determine the Extended Events equivalents", and add the predicates (filters) that you identified in the procedure "To determine the filters that were used in the script".</span></span>  
  
     <span data-ttu-id="3eddb-143">下列範例會使用 SQL 追蹤指令碼，其中包含 SQL:StmtStarting 和 SP:StmtCompleted 事件類別，連同工作階段識別碼和持續時間的篩選器。</span><span class="sxs-lookup"><span data-stu-id="3eddb-143">The following example uses a SQL Trace script that includes the SQL:StmtStarting and SP:StmtCompleted event classes, with filters for session ID and duration.</span></span> <span data-ttu-id="3eddb-144">＜若要判斷擴充事件同等項目＞程序中的查詢範例輸出傳回下列結果集：</span><span class="sxs-lookup"><span data-stu-id="3eddb-144">Sample output for the query in the "Determine the Extended Events equivalents" procedure returned the following result set:</span></span>  
  
    ```  
    Eventid  package_name  event                   columnid  action  
    44       sqlserver     sp_statement_starting   6         nt_username  
    44       sqlserver     sp_statement_starting   9         client_pid  
    44       sqlserver     sp_statement_starting   10        client_app_name  
    44       sqlserver     sp_statement_starting   11        server_principal_name  
    44       sqlserver     sp_statement_starting   12        session_id  
    45       sqlserver     sp_statement_completed  6         nt_username  
    45       sqlserver     sp_statement_completed  9         client_pid  
    45       sqlserver     sp_statement_completed  10        client_app_name  
    45       sqlserver     sp_statement_completed  11        server_principal_name  
    45       sqlserver     sp_statement_completed  12        session_id  
    ```  
  
     <span data-ttu-id="3eddb-145">若要將這個項目轉換成「擴充事件」同等項目，則會加入 sqlserver.sp_statement_starting 和 sqlserver.sp_statement_completed 事件，連同動作清單。</span><span class="sxs-lookup"><span data-stu-id="3eddb-145">To convert this to the Extended Events equivalent, the sqlserver.sp_statement_starting and the sqlserver.sp_statement_completed events are added, with a list of actions.</span></span> <span data-ttu-id="3eddb-146">包含述詞陳述式當做 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="3eddb-146">Predicate statements are included as WHERE clauses.</span></span>  
  
    ```sql
    ADD EVENT sqlserver.sp_statement_starting  
       (ACTION  
          (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
          )  
       WHERE sqlserver.session_id = 59   
       ),  
  
    ADD EVENT sqlserver.sp_statement_completed  
       (ACTION  
          (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
          )  
       WHERE sqlserver.session_id = 59 AND duration > 0  
       )  
    ```  
  
3.  <span data-ttu-id="3eddb-147">新增非同步檔案目標，使用您想要儲存輸出的位置來取代檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="3eddb-147">Add the asynchronous file target, replacing the file paths with the location where you want to save the output.</span></span> <span data-ttu-id="3eddb-148">當您指定檔案目標時，您必須包含記錄檔和中繼資料檔案路徑檔案。</span><span class="sxs-lookup"><span data-stu-id="3eddb-148">When specifying the file target, you must include a log file and metadata file path file.</span></span>  
  
    ```sql
    ADD TARGET package0.asynchronous_file_target(  
       SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
    ```  
  
## <a name="to-view-the-results"></a><span data-ttu-id="3eddb-149">若要檢視結果</span><span class="sxs-lookup"><span data-stu-id="3eddb-149">To view the results</span></span>  
  
1.  <span data-ttu-id="3eddb-150">您可以使用 sys.fn_xe_file_target_read_file 函數來檢視輸出。</span><span class="sxs-lookup"><span data-stu-id="3eddb-150">You can use the sys.fn_xe_file_target_read_file function to view the output.</span></span> <span data-ttu-id="3eddb-151">若要這樣做，請執行下列查詢，使用您指定的路徑來取代檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="3eddb-151">To do this, run the following query, replacing the file paths with the paths that you specified:</span></span>  
  
    ```sql
    SELECT *, CAST(event_data as XML) AS 'event_data_XML'  
    FROM sys.fn_xe_file_target_read_file('c:\temp\ExtendedEventsStoredProcs*.xel', 'c:\temp\ExtendedEventsStoredProcs*.xem', NULL, NULL);  
  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="3eddb-152">將事件資料轉換為 XML 是選擇性的動作。</span><span class="sxs-lookup"><span data-stu-id="3eddb-152">Casting the event data as XML is optional.</span></span>  
  
     <span data-ttu-id="3eddb-153">如需 sys.fn_xe_file_target_read_file 函數的詳細資訊，請參閱 [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3eddb-153">For more information about the sys.fn_xe_file_target_read_file function, see [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>  
  
    ```sql
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
       DROP EVENT SESSION [session_name] ON SERVER;  
    CREATE EVENT SESSION [session_name]  
    ON SERVER  
  
    ADD EVENT sqlserver.sp_statement_starting  
       (ACTION  
       (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
       )  
       WHERE sqlserver.session_id = 59   
       ),  
  
    ADD EVENT sqlserver.sp_statement_completed  
       (ACTION  
       (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
       )  
       WHERE sqlserver.session_id = 59 AND duration > 0  
       );  
  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
    ```  
  
## <a name="example"></a><span data-ttu-id="3eddb-154">範例</span><span class="sxs-lookup"><span data-stu-id="3eddb-154">Example</span></span>  
  
```sql
IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
   DROP EVENT SESSION [session_name] ON SERVER;  
CREATE EVENT SESSION [session_name]  
ON SERVER  
  
ADD EVENT sqlserver.sp_statement_starting  
   (ACTION  
   (  
      sqlserver.nt_username,  
      sqlserver.client_pid,  
      sqlserver.client_app_name,  
      sqlserver.server_principal_name,  
      sqlserver.session_id  
   )  
   WHERE sqlserver.session_id = 59   
   ),  
  
ADD EVENT sqlserver.sp_statement_completed  
   (ACTION  
   (  
      sqlserver.nt_username,  
      sqlserver.client_pid,  
      sqlserver.client_app_name,  
      sqlserver.server_principal_name,  
      sqlserver.session_id  
   )  
   WHERE sqlserver.session_id = 59 AND duration > 0  
   )  
  
ADD TARGET package0.asynchronous_file_target  
   (SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
```  
  
## <a name="see-also"></a><span data-ttu-id="3eddb-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eddb-155">See Also</span></span>  
 [<span data-ttu-id="3eddb-156">檢視同等於 SQL 追蹤事件類別的擴充事件</span><span class="sxs-lookup"><span data-stu-id="3eddb-156">View the Extended Events Equivalents to SQL Trace Event Classes</span></span>](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)  
  
  
