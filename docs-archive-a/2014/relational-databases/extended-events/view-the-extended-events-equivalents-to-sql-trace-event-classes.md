---
title: 檢視同等於 SQL 追蹤事件類別的擴充事件 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, extended events equivalents
- extended events [SQL Server], SQL Trace equivalents
- extended events [SQL Server], user configurable events
ms.assetid: 7f24104c-201d-4361-9759-f78a27936011
author: rothja
ms.author: jroth
ms.openlocfilehash: 37459359f9f6cb7e3951b705c4007477ec43e36a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686927"
---
# <a name="view-the-extended-events-equivalents-to-sql-trace-event-classes"></a><span data-ttu-id="35a9d-102">檢視同等於 SQL 追蹤事件類別的擴充事件項目</span><span class="sxs-lookup"><span data-stu-id="35a9d-102">View the Extended Events Equivalents to SQL Trace Event Classes</span></span>
  <span data-ttu-id="35a9d-103">如果您想要使用「擴充事件」來收集同等於 SQL 追蹤事件類別和資料行的事件資料，了解 SQL 追蹤事件如何對應到「擴充事件」事件和動作會非常實用。</span><span class="sxs-lookup"><span data-stu-id="35a9d-103">If you want to use Extended Events to collect event data that is equivalent to SQL Trace event classes and columns, it is useful to understand how the SQL Trace events map to Extended Events events and actions.</span></span>  
  
 <span data-ttu-id="35a9d-104">您可以使用下列程序來檢視同等於每一個 SQL 追蹤事件及其關聯資料行的「擴充事件」事件和動作。</span><span class="sxs-lookup"><span data-stu-id="35a9d-104">You can use the following procedure to view the Extended Events events and actions that are equivalent to each SQL Trace event and its associated columns.</span></span>  
  
## <a name="to-view-the-extended-events-equivalents-to-sql-trace-events-using-query-editor"></a><span data-ttu-id="35a9d-105">若要使用查詢編輯器檢視相當於 SQL 追蹤事件的擴充事件</span><span class="sxs-lookup"><span data-stu-id="35a9d-105">To view the Extended Events equivalents to SQL Trace events using Query Editor</span></span>  
  
-   <span data-ttu-id="35a9d-106">從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的查詢編輯器執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="35a9d-106">From Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], run the following query:</span></span>  
  
    ```  
    USE MASTER;  
    GO  
    SELECT DISTINCT  
       tb.trace_event_id,  
       te.name AS 'Event Class',  
       em.package_name AS 'Package',  
       em.xe_event_name AS 'XEvent Name',  
       tb.trace_column_id,  
       tc.name AS 'SQL Trace Column',  
       am.xe_action_name as 'Extended Events action'  
    FROM (sys.trace_events te LEFT OUTER JOIN sys.trace_xe_event_map em  
       ON te.trace_event_id = em.trace_event_id) LEFT OUTER JOIN sys.trace_event_bindings tb  
       ON em.trace_event_id = tb.trace_event_id LEFT OUTER JOIN sys.trace_columns tc  
       ON tb.trace_column_id = tc.trace_column_id LEFT OUTER JOIN sys.trace_xe_action_map am  
       ON tc.trace_column_id = am.trace_column_id  
    ORDER BY te.name, tc.name  
    ```  
  
 <span data-ttu-id="35a9d-107">當您檢視結果時，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="35a9d-107">When you view the results, note the following:</span></span>  
  
-   <span data-ttu-id="35a9d-108">如果事件類別資料行以外的所有其他資料行都傳回 NULL，表示並未從 SQL 追蹤移轉事件類別。</span><span class="sxs-lookup"><span data-stu-id="35a9d-108">If all columns return NULL except for the Event Class column, this indicates that the event class was not migrated from SQL Trace.</span></span>  
  
-   <span data-ttu-id="35a9d-109">如果只有擴充事件動作資料行中的值為 NULL，表示下列其中一個條件成立：</span><span class="sxs-lookup"><span data-stu-id="35a9d-109">If only the value in the Extended Events action column is NULL, this indicates that either of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="35a9d-110">SQL 追蹤資料行對應到與「擴充事件」事件相關聯的其中一個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="35a9d-110">The SQL Trace column maps to one of the data fields that is associated with the Extended Events event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="35a9d-111">每一個「擴充事件」事件都有一組預設資料欄位，這些欄位會自動包含在結果集內。</span><span class="sxs-lookup"><span data-stu-id="35a9d-111">Each Extended Events event has a default set of data fields that are automatically included in the result set.</span></span>  
  
    -   <span data-ttu-id="35a9d-112">此動作資料行並沒有有意義的「擴充事件」同等項目。</span><span class="sxs-lookup"><span data-stu-id="35a9d-112">The action column does not have a meaningful Extended Events equivalent.</span></span> <span data-ttu-id="35a9d-113">其中一個範例就是 SQL 追蹤中的 EventClass 資料行。</span><span class="sxs-lookup"><span data-stu-id="35a9d-113">An example of this is the EventClass column in SQL Trace.</span></span> <span data-ttu-id="35a9d-114">「擴充事件」中不需要此資料行，因為事件名稱有相同的用途。</span><span class="sxs-lookup"><span data-stu-id="35a9d-114">This column is not needed in Extended Events because the event name serves the same purpose.</span></span>  
  
-   <span data-ttu-id="35a9d-115">如果是使用者可設定的 SQL 追蹤事件類別 (透過 UserConfigurable:9 的 UserConfigurable:1)，擴充事件會使用單一事件來取代這些項目。</span><span class="sxs-lookup"><span data-stu-id="35a9d-115">For user configurable SQL Trace event classes (UserConfigurable:1 through UserConfigurable:9), Extended Events uses a single event to replace these.</span></span> <span data-ttu-id="35a9d-116">此事件命名為 user_event。</span><span class="sxs-lookup"><span data-stu-id="35a9d-116">The event is named user_event.</span></span> <span data-ttu-id="35a9d-117">這個事件是使用 sp_trace_generateevent 所引發，這與 SQL 追蹤所使用的預存程序相同。</span><span class="sxs-lookup"><span data-stu-id="35a9d-117">This event is raised by using sp_trace_generateevent, which is the same stored procedure that is used by SQL Trace.</span></span> <span data-ttu-id="35a9d-118">不論傳遞給預存程序的事件識別碼為何，都會傳回 user_event 事件。</span><span class="sxs-lookup"><span data-stu-id="35a9d-118">The user_event event is returned regardless of which event ID is passed to the stored procedure.</span></span> <span data-ttu-id="35a9d-119">但是，event_id 欄位會當作事件資料的一部分傳回。</span><span class="sxs-lookup"><span data-stu-id="35a9d-119">However, an event_id field is returned as part of the event data.</span></span> <span data-ttu-id="35a9d-120">這可讓您建立以事件識別碼為基礎的述詞。</span><span class="sxs-lookup"><span data-stu-id="35a9d-120">This enables you to build a predicate that is based on the event ID.</span></span> <span data-ttu-id="35a9d-121">例如，如果您在程式碼中使用 UserConfigurable:0 (事件識別碼 = 82)，您可以將 user_event 事件加入至工作階段中，並指定 'event_id = 82' 的述詞。</span><span class="sxs-lookup"><span data-stu-id="35a9d-121">For example, if you use UserConfigurable:0 (event ID = 82) in the code, you can add the user_event event to the session, and specify a predicate of 'event_id = 82'.</span></span> <span data-ttu-id="35a9d-122">因此，您不必變更程式碼，因為 sp_trace_generateevent 預存程序會產生擴充事件 user_event 事件及同等的 SQL 追蹤事件類別。</span><span class="sxs-lookup"><span data-stu-id="35a9d-122">Therefore, you do not have to change the code because the sp_trace_generateevent stored procedure generates the Extended Events user_event event, and the equivalent SQL Trace event class.</span></span>  
  
-   <span data-ttu-id="35a9d-123">如果事件類別資料行以外的所有其他資料行都傳回 NULL，表示並未從 SQL 追蹤移轉事件類別。</span><span class="sxs-lookup"><span data-stu-id="35a9d-123">If all columns return NULL except for the Event Class column, this indicates that the event class was not migrated from SQL Trace.</span></span>  
  
-   <span data-ttu-id="35a9d-124">如果只有擴充事件動作資料行中的值為 NULL，表示下列其中一個條件成立：</span><span class="sxs-lookup"><span data-stu-id="35a9d-124">If only the value in the Extended Events action column is NULL, this indicates that either of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="35a9d-125">SQL 追蹤資料行對應到與「擴充事件」事件相關聯的其中一個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="35a9d-125">The SQL Trace column maps to one of the data fields that is associated with the Extended Events event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="35a9d-126">每一個「擴充事件」事件都有一組預設資料欄位，這些欄位會自動包含在結果集內。</span><span class="sxs-lookup"><span data-stu-id="35a9d-126">Each Extended Events event has a default set of data fields that are automatically included in the result set.</span></span>  
  
    -   <span data-ttu-id="35a9d-127">此動作資料行並沒有有意義的「擴充事件」同等項目。</span><span class="sxs-lookup"><span data-stu-id="35a9d-127">The action column does not have a meaningful Extended Events equivalent.</span></span> <span data-ttu-id="35a9d-128">其中一個範例就是 SQL 追蹤中的 EventClass 資料行。</span><span class="sxs-lookup"><span data-stu-id="35a9d-128">An example of this is the EventClass column in SQL Trace.</span></span> <span data-ttu-id="35a9d-129">「擴充事件」中不需要此資料行，因為事件名稱有相同的用途。</span><span class="sxs-lookup"><span data-stu-id="35a9d-129">This column is not needed in Extended Events because the event name serves the same purpose.</span></span>  
  
-   <span data-ttu-id="35a9d-130">如果是使用者可設定的 SQL 追蹤事件類別 (透過 UserConfigurable:9 的 UserConfigurable:1)，擴充事件會使用單一事件來取代這些項目。</span><span class="sxs-lookup"><span data-stu-id="35a9d-130">For user configurable SQL Trace event classes (UserConfigurable:1 through UserConfigurable:9), Extended Events uses a single event to replace these.</span></span> <span data-ttu-id="35a9d-131">此事件命名為 user_event。</span><span class="sxs-lookup"><span data-stu-id="35a9d-131">The event is named user_event.</span></span> <span data-ttu-id="35a9d-132">這個事件是使用 sp_trace_generateevent 所引發，這與 SQL 追蹤所使用的預存程序相同。</span><span class="sxs-lookup"><span data-stu-id="35a9d-132">This event is raised by using sp_trace_generateevent, which is the same stored procedure that is used by SQL Trace.</span></span> <span data-ttu-id="35a9d-133">不論傳遞給預存程序的事件識別碼為何，都會傳回 user_event 事件。</span><span class="sxs-lookup"><span data-stu-id="35a9d-133">The user_event event is returned regardless of which event ID is passed to the stored procedure.</span></span> <span data-ttu-id="35a9d-134">但是，event_id 欄位會當作事件資料的一部分傳回。</span><span class="sxs-lookup"><span data-stu-id="35a9d-134">However, an event_id field is returned as part of the event data.</span></span> <span data-ttu-id="35a9d-135">這可讓您建立以事件識別碼為基礎的述詞。</span><span class="sxs-lookup"><span data-stu-id="35a9d-135">This enables you to build a predicate that is based on the event ID.</span></span> <span data-ttu-id="35a9d-136">例如，如果您在程式碼中使用 UserConfigurable:0 (事件識別碼 = 82)，您可以將 user_event 事件加入至工作階段中，並指定 'event_id = 82' 的述詞。</span><span class="sxs-lookup"><span data-stu-id="35a9d-136">For example, if you use UserConfigurable:0 (event ID = 82) in the code, you can add the user_event event to the session, and specify a predicate of 'event_id = 82'.</span></span> <span data-ttu-id="35a9d-137">因此，您不必變更程式碼，因為 sp_trace_generateevent 預存程序會產生擴充事件 user_event 事件及同等的 SQL 追蹤事件類別。</span><span class="sxs-lookup"><span data-stu-id="35a9d-137">Therefore, you do not have to change the code because the sp_trace_generateevent stored procedure generates the Extended Events user_event event, and the equivalent SQL Trace event class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a9d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35a9d-138">See Also</span></span>  
 [<span data-ttu-id="35a9d-139">sp_trace_generateevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="35a9d-139">sp_trace_generateevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)  
  
  
