---
title: 使用擴充事件監視系統活動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- extended events [SQL Server], monitoring system activity
ms.assetid: d83ad88f-818c-49fe-a9a9-299f704fca53
author: rothja
ms.author: jroth
ms.openlocfilehash: d847d156d8244ede533e684c9e6b753d7d7b5047
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585410"
---
# <a name="monitor-system-activity-using-extended-events"></a><span data-ttu-id="dfc72-102">使用擴充事件監視系統活動</span><span class="sxs-lookup"><span data-stu-id="dfc72-102">Monitor System Activity Using Extended Events</span></span>
  <span data-ttu-id="dfc72-103">此程序說明如何搭配 Windows 事件追蹤 (ETW) 來使用擴充的事件，以監視系統活動。</span><span class="sxs-lookup"><span data-stu-id="dfc72-103">This procedure illustrates how Extended Events can be used with Event Tracing for Windows (ETW) to monitor system activity.</span></span> <span data-ttu-id="dfc72-104">此程序也會示範如何使用 CREATE EVENT SESSION、ALTER EVENT SESSION 和 DROP EVENT SESSION 陳述式。</span><span class="sxs-lookup"><span data-stu-id="dfc72-104">The procedure also shows how the CREATE EVENT SESSION, ALTER EVENT SESSION, and DROP EVENT SESSION statements are used.</span></span>  
  
 <span data-ttu-id="dfc72-105">完成這些工作需要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中使用查詢編輯器來進行以下程序。</span><span class="sxs-lookup"><span data-stu-id="dfc72-105">Accomplishing these tasks involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span> <span data-ttu-id="dfc72-106">此程序也需要使用命令提示字元來執行 ETW 命令。</span><span class="sxs-lookup"><span data-stu-id="dfc72-106">The procedure also requires using the command prompt to run ETW commands.</span></span>  
  
### <a name="to-monitor-system-activity-using-extended-events"></a><span data-ttu-id="dfc72-107">使用擴充的事件監視系統活動</span><span class="sxs-lookup"><span data-stu-id="dfc72-107">To monitor system activity using Extended Events</span></span>  
  
1.  <span data-ttu-id="dfc72-108">在查詢編輯器中，發出下列陳述式來建立事件工作階段及加入兩個事件。</span><span class="sxs-lookup"><span data-stu-id="dfc72-108">In Query Editor, issue the following statements to create an event session and add two events.</span></span> <span data-ttu-id="dfc72-109">這些 checkpoint_begin 和 checkpoint_end 事件會在資料庫中斷點的開頭和結尾引發。</span><span class="sxs-lookup"><span data-stu-id="dfc72-109">These events, checkpoint_begin and checkpoint_end, fire at the beginning and end of a database checkpoint.</span></span>  
  
    ```  
    CREATE EVENT SESSION test0  
    ON SERVER  
    ADD EVENT sqlserver.checkpoint_begin,  
    ADD EVENT sqlserver.checkpoint_end  
    WITH (MAX_DISPATCH_LATENCY = 1 SECONDS)  
    go  
    ```  
  
2.  <span data-ttu-id="dfc72-110">加入具有 32 個值區的值區目標，以根據資料庫識別碼計算中斷點的數目。</span><span class="sxs-lookup"><span data-stu-id="dfc72-110">Add the bucketing target with 32 buckets to count the number of checkpoints based on the database ID.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.histogram  
    (  
          SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id'  
    )  
    go  
    ```  
  
3.  <span data-ttu-id="dfc72-111">發出下列陳述式來加入 ETW 目標，</span><span class="sxs-lookup"><span data-stu-id="dfc72-111">Issue the following statements to add the ETW target.</span></span> <span data-ttu-id="dfc72-112">如此將可讓您看到開頭和結束事件，這可用來判斷中斷點所花的時間長度。</span><span class="sxs-lookup"><span data-stu-id="dfc72-112">This will enable you to see the begin and end events, which is used to determine how long the checkpoint takes.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.etw_classic_sync_target  
    go  
    ```  
  
4.  <span data-ttu-id="dfc72-113">發出下列陳述式，以啟動工作階段及開始事件收集。</span><span class="sxs-lookup"><span data-stu-id="dfc72-113">Issue the following statements to start the session and begin event collection.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = start  
    go  
    ```  
  
5.  <span data-ttu-id="dfc72-114">發出下列陳述式來引發三個事件。</span><span class="sxs-lookup"><span data-stu-id="dfc72-114">Issue the following statements to cause three events to fire.</span></span>  
  
    ```  
    USE tempdb  
          checkpoint  
    go  
    USE master  
          checkpoint  
          checkpoint  
    go  
    ```  
  
6.  <span data-ttu-id="dfc72-115">發出下列陳述式來檢視事件計數。</span><span class="sxs-lookup"><span data-stu-id="dfc72-115">Issue the following statements to view the event counts.</span></span>  
  
    ```  
    SELECT CAST(xest.target_data AS xml) Bucketizer_Target_Data_in_XML  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'test0'  
    go  
    ```  
  
7.  <span data-ttu-id="dfc72-116">在命令提示字元下，發出下列命令來檢視 ETW 資料。</span><span class="sxs-lookup"><span data-stu-id="dfc72-116">At the command prompt, issue the following commands to view the ETW data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dfc72-117">若要取得 **tracerpt** 命令的說明，請在命令提示字元上輸入 `tracerpt /?`。</span><span class="sxs-lookup"><span data-stu-id="dfc72-117">To get help for the **tracerpt** command, at the command prompt, enter `tracerpt /?`.</span></span>  
  
    ```  
    logman query -ets --- List the ETW sessions. This is optional.  
    logman update XE_DEFAULT_ETW_SESSION -fd -ets --- Flush the ETW log.  
    tracerpt %temp%\xeetw.etl -o xeetw.txt --- Dump the events so they can be seen.  
    ```  
  
8.  <span data-ttu-id="dfc72-118">發出下列陳述式，以停止事件工作階段，並從伺服器中將它移除。</span><span class="sxs-lookup"><span data-stu-id="dfc72-118">Issue the following statements to stop the event session and remove it from the server.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = STOP  
    go  
  
    DROP EVENT SESSION test0  
    ON SERVER  
    go  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dfc72-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfc72-119">See Also</span></span>  
 <span data-ttu-id="dfc72-120">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dfc72-120">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="dfc72-121">[ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dfc72-121">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 <span data-ttu-id="dfc72-122">[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dfc72-122">[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="dfc72-123">擴充的事件目錄檢視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dfc72-123">Extended Events Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql)  
 <span data-ttu-id="dfc72-124">[擴充的事件動態管理檢視](../views/views.md) </span><span class="sxs-lookup"><span data-stu-id="dfc72-124">[Extended Events Dynamic Management Views](../views/views.md) </span></span>  
 [<span data-ttu-id="dfc72-125">SQL Server 擴充的事件目標</span><span class="sxs-lookup"><span data-stu-id="dfc72-125">SQL Server Extended Events Targets</span></span>](../../database-engine/sql-server-extended-events-targets.md)  
  
  
