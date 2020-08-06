---
title: 使用查詢編輯器建立擴充事件會話 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- create extended events session
- extended events [SQL Server], create session
ms.assetid: cba0e02b-b201-4863-bf1b-9164e68e5fa8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 648370ecdd2938b6fb425955dc02da8960f884c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596261"
---
# <a name="create-an-extended-events-session-using-query-editor"></a><span data-ttu-id="84e8f-102">使用查詢編輯器建立擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="84e8f-102">Create an Extended Events Session Using Query Editor</span></span>
  <span data-ttu-id="84e8f-103">您可以使用查詢編輯器來建立擴充事件工作階段，也可以在物件總管中建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="84e8f-103">You can create an Extended Events session by using the Query Editor, or you can create a session in Object Explorer.</span></span> <span data-ttu-id="84e8f-104">在物件總管中，擴充事件提供兩個使用者介面，您可以用來建立、修改及查看事件會話資料，此嚮導會引導您完成事件會話的建立程式，以及提供更多更先進設定選項的新會話 UI。</span><span class="sxs-lookup"><span data-stu-id="84e8f-104">In Object Explorer, Extended Events provides two user interfaces you can use to create, modify, and view event session data - a wizard that guides you through the event session creation process, and a New Session UI that provides more advanced configuration options.</span></span> <span data-ttu-id="84e8f-105">您可以建立擴充事件工作階段來診斷 SQL Server 追蹤，以便解決下列問題：</span><span class="sxs-lookup"><span data-stu-id="84e8f-105">You can create Extended Events sessions to diagnose SQL Server tracing, which enables you to resolve issues such as the following:</span></span>  
  
-   <span data-ttu-id="84e8f-106">尋找最費時的查詢</span><span class="sxs-lookup"><span data-stu-id="84e8f-106">Find your most expensive queries</span></span>  
  
-   <span data-ttu-id="84e8f-107">尋找導致閂鎖競爭的根本原因</span><span class="sxs-lookup"><span data-stu-id="84e8f-107">Find root causes of latch contention</span></span>  
  
-   <span data-ttu-id="84e8f-108">尋找封鎖其他查詢的查詢</span><span class="sxs-lookup"><span data-stu-id="84e8f-108">Find a query that is blocking other queries</span></span>  
  
-   <span data-ttu-id="84e8f-109">疑難排解因重新編譯查詢所致的過度使用 CPU 的問題</span><span class="sxs-lookup"><span data-stu-id="84e8f-109">Troubleshoot excessive CPU usage caused by query recompilation</span></span>  
  
-   <span data-ttu-id="84e8f-110">疑難排解死結</span><span class="sxs-lookup"><span data-stu-id="84e8f-110">Troubleshoot deadlocks</span></span>  
  
 <span data-ttu-id="84e8f-111">如需如何使用 [新增工作階段精靈] 建立擴充事件工作階段的相關資訊，請參閱[使用精靈建立擴充事件工作階段 &#40;物件總管&#41;](../ssms/object/object-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="84e8f-111">For information about how to create an Extended Events session using the New Session Wizard, see [Create an Extended Events Session Using the Wizard &#40;Object Explorer&#41;](../ssms/object/object-explorer.md).</span></span> <span data-ttu-id="84e8f-112">如需如何使用 [新增工作階段] UI 建立擴充事件工作階段的相關資訊，請參閱 [Quick Start: Extended events in SQL Server](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) (快速入門：SQL Server擴充事件)。</span><span class="sxs-lookup"><span data-stu-id="84e8f-112">For information about how to create an Extended Events session using the New Session UI, see [Create an Extended Events Session Using the New Session Dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md).</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="84e8f-113">權限</span><span class="sxs-lookup"><span data-stu-id="84e8f-113">Permissions</span></span>  
 <span data-ttu-id="84e8f-114">若要建立「擴充事件」工作階段，您必須擁有 ALTER ANY EVENT SESSION 權限。</span><span class="sxs-lookup"><span data-stu-id="84e8f-114">To create an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
## <a name="creating-an-extended-events-session-using-query-editor"></a><span data-ttu-id="84e8f-115">使用查詢編輯器建立擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="84e8f-115">Creating an Extended Events session using Query Editor</span></span>  
  
#### <a name="to-create-an-extended-events-session"></a><span data-ttu-id="84e8f-116">若要建立擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="84e8f-116">To create an Extended Events session</span></span>  
  
1.  <span data-ttu-id="84e8f-117">下列程序示範如何在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中使用查詢編輯器來建立「擴充事件」工作階段。</span><span class="sxs-lookup"><span data-stu-id="84e8f-117">The following procedure shows how to create an Extended Events session by using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="84e8f-118">決定您想要在工作階段中使用的事件。</span><span class="sxs-lookup"><span data-stu-id="84e8f-118">Determine which events that you want to use in the session.</span></span> <span data-ttu-id="84e8f-119">若要查看所有可用的事件，連同關鍵字與通道，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="84e8f-119">To see all the events that are available, together with the keyword and channel, use the following query:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84e8f-120">如需關鍵字和通道的相關資訊，請參閱 [SQL Server 擴充事件封裝](../relational-databases/extended-events/sql-server-extended-events-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="84e8f-120">For information about keywords and channels, see [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).</span></span>  
  
    ```  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
       (  
       SELECT event_package = o.package_guid, o.description,   
       event=c.object_name, channel = v.map_value  
       FROM sys.dm_xe_objects o  
       LEFT JOIN sys.dm_xe_object_columns c ON o.name = c.object_name  
       INNER JOIN sys.dm_xe_map_values v ON c.type_name = v.name   
       AND c.column_value = cast(v.map_key AS nvarchar)  
       WHERE object_type = 'event' AND (c.name = 'CHANNEL' or c.name IS NULL)  
       ) c LEFT JOIN   
       (  
       SELECT event_package = c.object_package_guid, event = c.object_name,   
       keyword = v.map_value  
       FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
       ON c.type_name = v.name AND c.column_value = v.map_key   
       AND c.type_package_guid = v.object_package_guid  
       INNER JOIN sys.dm_xe_objects o ON o.name = c.object_name   
       AND o.package_guid = c.object_package_guid  
       WHERE object_type = 'event' AND c.name = 'KEYWORD'   
       ) k  
       ON  
       k.event_package = c.event_package AND (k.event=c.event or k.event IS NULL)  
       INNER JOIN sys.dm_xe_packages p ON p.guid = c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
2.  <span data-ttu-id="84e8f-121">在新的查詢視窗中，加入下列陳述式來建立事件工作階段，以您想要使用的工作階段名稱來取代 *session_name* 。</span><span class="sxs-lookup"><span data-stu-id="84e8f-121">In a new query window, add the following statements to create an event session, replacing *session_name* with the session name that you want to use:</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="84e8f-122">這個程序的步驟 2 到 6 會描述事件工作階段定義的每個區段。</span><span class="sxs-lookup"><span data-stu-id="84e8f-122">Steps 2 through 6 of this procedure describe each section of the event session definition.</span></span> <span data-ttu-id="84e8f-123">在執行之前，您會將所有陳述式加入到單一查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="84e8f-123">You would add all the statements to a single query window before executing.</span></span> <span data-ttu-id="84e8f-124">如需完整範例，請參閱本主題的＜範例＞一節。</span><span class="sxs-lookup"><span data-stu-id="84e8f-124">For a full example, see the Example section of this topic.</span></span>  
  
    ```  
    CREATE EVENT SESSION session_name   
    ON SERVER  
    ```  
  
3.  <span data-ttu-id="84e8f-125">使用以下格式加入您想要監視的事件： *package_name*.*event_name*。</span><span class="sxs-lookup"><span data-stu-id="84e8f-125">Add the events that you want to monitor, in the format *package_name*.*event_name*.</span></span> <span data-ttu-id="84e8f-126">針對每個事件，加入與下列相似的一行：</span><span class="sxs-lookup"><span data-stu-id="84e8f-126">For each event, add a line similar to the following:</span></span>  
  
    ```  
    ADD EVENT package_name.event_name  
    ```  
  
     <span data-ttu-id="84e8f-127">例如：</span><span class="sxs-lookup"><span data-stu-id="84e8f-127">For example:</span></span>  
  
    ```  
    ADD EVENT sqlserver.file_read_completed,  
    ADD EVENT sqlserver.file_write_completed  
    ```  
  
4.  <span data-ttu-id="84e8f-128">(選擇性) 加入事件之後，您可以加入要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="84e8f-128">(Optional) After you add an event, you can add actions to take.</span></span> <span data-ttu-id="84e8f-129">您也可以加入述詞。</span><span class="sxs-lookup"><span data-stu-id="84e8f-129">You can also add predicates.</span></span> <span data-ttu-id="84e8f-130">述詞是用來建立目標何時應該耗用事件資訊的準則。</span><span class="sxs-lookup"><span data-stu-id="84e8f-130">Predicates are used to establish criteria for when the event information should be consumed by the target.</span></span> <span data-ttu-id="84e8f-131">動作是使用 ACTION 子句加入，而述詞則是使用 WHERE 子句加入。</span><span class="sxs-lookup"><span data-stu-id="84e8f-131">Actions are added by using an ACTION clause, and predicates are added by using a WHERE clause.</span></span> <span data-ttu-id="84e8f-132">例如，若要加入動作和述詞，其中 [!INCLUDE[tsql](../includes/tsql-md.md)] 文字是針對 sqlserver.file_read_completed 事件所擷取，且檔案識別碼等於 1，您可以包含下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="84e8f-132">For example, to add an action and predicate where the [!INCLUDE[tsql](../includes/tsql-md.md)] text is captured for the sqlserver.file_read_completed event, where the file ID equals 1, you would include the following statement:</span></span>  
  
    ```  
    ADD EVENT sqlserver.file_read_completed  
       (ACTION (sqlserver.sql_text)  
       WHERE file_id = 1),  
    ```  
  
    -   <span data-ttu-id="84e8f-133">若要檢視有哪些動作可用，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="84e8f-133">To view which actions are available, use the following query:</span></span>  
  
        ```  
        SELECT p.name AS 'package_name', xo.name AS 'action_name', xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'action'  
        AND (xo.capabilities & 1 = 0   
        OR xo.capabilities IS NULL)  
        ORDER BY p.name, xo.name  
        ```  
  
    -   <span data-ttu-id="84e8f-134">若要檢視哪些述詞可供事件使用，請使用下列查詢，以您想要加入述詞的事件名稱取代 *event_name* ：</span><span class="sxs-lookup"><span data-stu-id="84e8f-134">To view which predicates are available for an event, use the following query, replacing *event_name* with the name of the event for which you want to add a predicate:</span></span>  
  
        ```  
        SELECT *  
        FROM sys.dm_xe_object_columns  
        WHERE object_name = 'event_name'  
        AND column_type = 'data'  
        ```  
  
         <span data-ttu-id="84e8f-135">例如：</span><span class="sxs-lookup"><span data-stu-id="84e8f-135">For example:</span></span>  
  
        ```  
        SELECT *   
        FROM sys.dm_xe_object_columns   
        WHERE object_name = 'file_read_completed'  
        AND column_type = 'data'  
        ```  
  
         <span data-ttu-id="84e8f-136">請注意，您也可以加入全域述詞來源。</span><span class="sxs-lookup"><span data-stu-id="84e8f-136">Be aware that you can also add global predicate sources.</span></span> <span data-ttu-id="84e8f-137">全域述詞來源可在任何述詞運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="84e8f-137">A global predicate source can be used in any predicate expression.</span></span> <span data-ttu-id="84e8f-138">若要檢視有哪些全域述詞來源可用，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="84e8f-138">To view which global predicate sources are available, use the following query:</span></span>  
  
        ```  
        SELECT p.name AS package_name, xo.name AS predicate_name  
           , xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'pred_source'  
        ORDER BY p.name, xo.name  
        ```  
  
         <span data-ttu-id="84e8f-139">例如，您可以使用下列述詞運算式指定，在某個事件發生前五次時，才應該收集此事件的資料。</span><span class="sxs-lookup"><span data-stu-id="84e8f-139">For example, you could use the following predicate expression to specify that data should only be collected for an event the first five times that an event occurs.</span></span>  
  
        ```  
        WHERE package0.counter <= 5  
        ```  
  
5.  <span data-ttu-id="84e8f-140">加入所要的目標，其中將會處理及耗用事件資料。</span><span class="sxs-lookup"><span data-stu-id="84e8f-140">Add the desired target, where the event data will be processed and consumed.</span></span> <span data-ttu-id="84e8f-141">請使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="84e8f-141">Use the following format:</span></span>  
  
    ```  
    ADD TARGET package_name.target_name  
    ```  
  
     <span data-ttu-id="84e8f-142">下列範例會加入非同步檔案目標：</span><span class="sxs-lookup"><span data-stu-id="84e8f-142">The following example adds the asynchronous file target:</span></span>  
  
    ```  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
    ```  
  
     <span data-ttu-id="84e8f-143">若要檢視可用目標的清單，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="84e8f-143">To view the list of available targets, use the following query:</span></span>  
  
    ```  
    SELECT p.name AS 'package_name', xo.name AS 'target_name'  
       , xo.description, xo.object_type   
    FROM sys.dm_xe_objects AS xo  
    JOIN sys.dm_xe_packages AS p  
       ON xo.package_guid = p.guid  
    WHERE xo.object_type = 'target'  
    AND (xo.capabilities & 1 = 0  
    OR xo.capabilities IS NULL)  
    ORDER BY p.name, xo.name  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="84e8f-144">如需不同目標類型的相關資訊，請參閱 [SQL Server 擴充的事件目標](../../2014/database-engine/sql-server-extended-events-targets.md)。</span><span class="sxs-lookup"><span data-stu-id="84e8f-144">For information about the different target types, see [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).</span></span>  
  
6.  <span data-ttu-id="84e8f-145">檢閱並加入任何其他組態選項。</span><span class="sxs-lookup"><span data-stu-id="84e8f-145">Review and add any additional configuration options.</span></span> <span data-ttu-id="84e8f-146">例如，您可以設定選項，例如事件保留模式、事件在記憶體中緩衝處理多久，或是當 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 啟動時事件工作階段是否應該自動啟動。</span><span class="sxs-lookup"><span data-stu-id="84e8f-146">For example, you can configure options such as the event retention mode, how long events are buffered in memory, or whether the event session should start automatically when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="84e8f-147">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) 主題會描述這些選項。</span><span class="sxs-lookup"><span data-stu-id="84e8f-147">The options are described in the topic [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql).</span></span> <span data-ttu-id="84e8f-148">請注意，如果未指定這些選項，就會指派預設值。</span><span class="sxs-lookup"><span data-stu-id="84e8f-148">Be aware that default values are assigned if these options are not specified.</span></span>  
  
7.  <span data-ttu-id="84e8f-149">啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="84e8f-149">Start the session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84e8f-150">如需有關如何檢視工作階段結果的詳細資訊，請參閱您在《線上叢書》的 [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) (SQL Server 擴充事件目標) 節點中所使用之目標類型的對應主題。</span><span class="sxs-lookup"><span data-stu-id="84e8f-150">For more information about how to view the session results, see the corresponding topic for the target type that you used in the [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) node of Books Online.</span></span>  
  
 <span data-ttu-id="84e8f-151">下列範例會建立名為 IOActivity 的「擴充事件」工作階段來擷取下列資訊：</span><span class="sxs-lookup"><span data-stu-id="84e8f-151">The following example creates an Extended Events session named IOActivity that captures the following information:</span></span>  
  
-   <span data-ttu-id="84e8f-152">已完成檔案讀取的事件資料，包括檔案讀取的相關 [!INCLUDE[tsql](../includes/tsql-md.md)] 文字，其中檔案識別碼等於 1。</span><span class="sxs-lookup"><span data-stu-id="84e8f-152">Event data for completed file reads, including the associated [!INCLUDE[tsql](../includes/tsql-md.md)] text for file reads where the file ID is equal to 1.</span></span>  
  
-   <span data-ttu-id="84e8f-153">已完成檔案寫入的事件資料。</span><span class="sxs-lookup"><span data-stu-id="84e8f-153">Event data for completed file writes.</span></span>  
  
-   <span data-ttu-id="84e8f-154">當資料從記錄檔快取寫入實體記錄檔時的事件資料。</span><span class="sxs-lookup"><span data-stu-id="84e8f-154">Event data for when data is written from the log cache to the physical log file.</span></span>  
  
 <span data-ttu-id="84e8f-155">工作階段會將輸出傳送到檔案目標。</span><span class="sxs-lookup"><span data-stu-id="84e8f-155">The session sends the output to a file target.</span></span>  
  
```  
CREATE EVENT SESSION IOActivity  
ON SERVER  
  
ADD EVENT sqlserver.file_read_completed  
   (  
   ACTION (sqlserver.sql_text)  
   WHERE file_id = 1),  
ADD EVENT sqlserver.file_write_completed,  
ADD EVENT sqlserver.databases_log_flush  
  
ADD TARGET package0.asynchronous_file_target   
   (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
```  
  
## <a name="see-also"></a><span data-ttu-id="84e8f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84e8f-156">See Also</span></span>  
 <span data-ttu-id="84e8f-157">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84e8f-157">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="84e8f-158">[SQL Server 擴充的事件目標](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="84e8f-158">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 [<span data-ttu-id="84e8f-159">SQL Server 擴充的事件套件</span><span class="sxs-lookup"><span data-stu-id="84e8f-159">SQL Server Extended Events Packages</span></span>](../relational-databases/extended-events/sql-server-extended-events-packages.md)  
  
  
