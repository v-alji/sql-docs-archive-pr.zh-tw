---
title: 事件配對目標 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- pairing target [SQL Server extended events]
- event pairing target
- targets [SQL Server extended events], pairing target
ms.assetid: 3c87dcfb-543a-4bd8-a73d-1390bdf4ffa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a1a6beb1c6996e6e12f16c4555fd9dfcab97617d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701602"
---
# <a name="event-pairing-target"></a><span data-ttu-id="c672f-102">事件配對目標</span><span class="sxs-lookup"><span data-stu-id="c672f-102">Event Pairing Target</span></span>
  <span data-ttu-id="c672f-103">事件配對目標會使用每個事件中存在之一個或多個資料行來比對兩個事件。</span><span class="sxs-lookup"><span data-stu-id="c672f-103">The event pairing target matches two events using one or more columns of data that are present in each event.</span></span> <span data-ttu-id="c672f-104">許多事件都是以成對的形式出現，例如鎖定取得和鎖定釋放。</span><span class="sxs-lookup"><span data-stu-id="c672f-104">Many events come in pairs, for example, lock acquires and lock releases.</span></span> <span data-ttu-id="c672f-105">當事件序列配對之後，會捨棄這兩個事件。</span><span class="sxs-lookup"><span data-stu-id="c672f-105">After an event sequence is paired, both events are discarded.</span></span> <span data-ttu-id="c672f-106">捨棄相符的事件組可讓您輕鬆偵測尚未釋放的鎖定取得。</span><span class="sxs-lookup"><span data-stu-id="c672f-106">Discarding matched sets allows for easy detection of lock acquisitions that have not been released.</span></span>  
  
 <span data-ttu-id="c672f-107">藉由使用事件層級的篩選，配對目標可以只用來擷取不符合預設準則的事件。</span><span class="sxs-lookup"><span data-stu-id="c672f-107">By using event-level filters, the pairing target can be used to only capture events that do not match pre-set criteria.</span></span>  
  
 <span data-ttu-id="c672f-108">當您使用事件配對目標時，可以選擇將要比對的兩個事件，以及比對作業執行所在的資料行序列。</span><span class="sxs-lookup"><span data-stu-id="c672f-108">When you use the event pairing target, you can choose two events that will be matched, together with a sequence of columns to perform the matching on.</span></span> <span data-ttu-id="c672f-109">此序列中的所有資料行都必須有相同的類型。</span><span class="sxs-lookup"><span data-stu-id="c672f-109">All the columns in this sequence must be of the same type.</span></span>  
  
 <span data-ttu-id="c672f-110">下表說明用來設定事件配對的可用選項。</span><span class="sxs-lookup"><span data-stu-id="c672f-110">The following table describes the available options for configuring event pairing.</span></span>  
  
|<span data-ttu-id="c672f-111">選項</span><span class="sxs-lookup"><span data-stu-id="c672f-111">Option</span></span>|<span data-ttu-id="c672f-112">允許的值</span><span class="sxs-lookup"><span data-stu-id="c672f-112">Allowed values</span></span>|<span data-ttu-id="c672f-113">描述</span><span class="sxs-lookup"><span data-stu-id="c672f-113">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="c672f-114">begin_event</span><span class="sxs-lookup"><span data-stu-id="c672f-114">begin_event</span></span>|<span data-ttu-id="c672f-115">存在於目前工作階段中的任何事件名稱。</span><span class="sxs-lookup"><span data-stu-id="c672f-115">Any event name that is present in the current session.</span></span>|<span data-ttu-id="c672f-116">指定配對序列中之開頭事件的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="c672f-116">The event name specifying the beginning event in a paired sequence.</span></span>|  
|<span data-ttu-id="c672f-117">end_event</span><span class="sxs-lookup"><span data-stu-id="c672f-117">end_event</span></span>|<span data-ttu-id="c672f-118">存在於目前工作階段中的任何事件名稱。</span><span class="sxs-lookup"><span data-stu-id="c672f-118">Any event name that is present in the current session.</span></span>|<span data-ttu-id="c672f-119">指定配對序列中之結尾事件的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="c672f-119">The event name specifying the ending event in a paired sequence.</span></span>|  
|<span data-ttu-id="c672f-120">begin_matching_columns</span><span class="sxs-lookup"><span data-stu-id="c672f-120">begin_matching_columns</span></span>|<span data-ttu-id="c672f-121">以逗號分隔且排序的資料行名稱清單。</span><span class="sxs-lookup"><span data-stu-id="c672f-121">A comma-delimited, ordered list of column names.</span></span>|<span data-ttu-id="c672f-122">要執行比對的資料行。</span><span class="sxs-lookup"><span data-stu-id="c672f-122">The columns to perform matching on.</span></span>|  
|<span data-ttu-id="c672f-123">end_matching_columns</span><span class="sxs-lookup"><span data-stu-id="c672f-123">end_matching_columns</span></span>|<span data-ttu-id="c672f-124">以逗號分隔且排序的資料行名稱清單。</span><span class="sxs-lookup"><span data-stu-id="c672f-124">A comma-delimited, ordered list of column names.</span></span>|<span data-ttu-id="c672f-125">要執行比對的資料行。</span><span class="sxs-lookup"><span data-stu-id="c672f-125">The columns to perform matching on.</span></span>|  
|<span data-ttu-id="c672f-126">begin_matching_actions</span><span class="sxs-lookup"><span data-stu-id="c672f-126">begin_matching_actions</span></span>|<span data-ttu-id="c672f-127">以逗號分隔且排序的動作清單。</span><span class="sxs-lookup"><span data-stu-id="c672f-127">A comma-delimited, ordered list of actions.</span></span>|<span data-ttu-id="c672f-128">要執行比對的動作。</span><span class="sxs-lookup"><span data-stu-id="c672f-128">The actions to perform matching on.</span></span>|  
|<span data-ttu-id="c672f-129">end_matching_actions</span><span class="sxs-lookup"><span data-stu-id="c672f-129">end_matching_actions</span></span>|<span data-ttu-id="c672f-130">以逗號分隔且排序的動作清單。</span><span class="sxs-lookup"><span data-stu-id="c672f-130">A comma-delimited, ordered list of actions.</span></span>|<span data-ttu-id="c672f-131">要執行比對的動作。</span><span class="sxs-lookup"><span data-stu-id="c672f-131">The actions to perform matching on.</span></span>|  
|<span data-ttu-id="c672f-132">respond_to_memory_pressure</span><span class="sxs-lookup"><span data-stu-id="c672f-132">respond_to_memory_pressure</span></span>|<span data-ttu-id="c672f-133">下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="c672f-133">One of the following values:</span></span><br /><br /> <span data-ttu-id="c672f-134">0 = 不回應。</span><span class="sxs-lookup"><span data-stu-id="c672f-134">0 = Do not respond.</span></span><br /><br /> <span data-ttu-id="c672f-135">1 = 當有記憶體不足的壓力時，停止將新的遺棄項目加入清單中。</span><span class="sxs-lookup"><span data-stu-id="c672f-135">1 = Stop adding new orphans to the list when there is memory pressure.</span></span>|<span data-ttu-id="c672f-136">對記憶體事件的目標回應。</span><span class="sxs-lookup"><span data-stu-id="c672f-136">The target response to memory events.</span></span> <span data-ttu-id="c672f-137">如果設定為 1，而且伺服器的記憶體很少，則會移除正在維護且未成對的資訊。</span><span class="sxs-lookup"><span data-stu-id="c672f-137">If set to 1 and the server is low on memory, unpaired information that is being maintained is removed.</span></span>|  
|<span data-ttu-id="c672f-138">max_orphans</span><span class="sxs-lookup"><span data-stu-id="c672f-138">max_orphans</span></span>||<span data-ttu-id="c672f-139">指定目標中將收集的未配對事件總數。</span><span class="sxs-lookup"><span data-stu-id="c672f-139">Specifies the total number of unpaired events that will be collected in the target.</span></span> <span data-ttu-id="c672f-140">一旦達到此限制，就會根據先入先出 (FIFO) 移除未配對的事件。</span><span class="sxs-lookup"><span data-stu-id="c672f-140">Once the limit is reached, unpaired events are removed on a first-in, first-out (FIFO) basis.</span></span> <span data-ttu-id="c672f-141">預設值 = 10,000。</span><span class="sxs-lookup"><span data-stu-id="c672f-141">Default = 10,000.</span></span>|  
  
 <span data-ttu-id="c672f-142">所有與事件有關的資料都會擷取，並儲存起來供將來配對。</span><span class="sxs-lookup"><span data-stu-id="c672f-142">All the data associated with an event is captured and stored for future pairing.</span></span> <span data-ttu-id="c672f-143">此外，也會收集動作所加入的資料。</span><span class="sxs-lookup"><span data-stu-id="c672f-143">In addition, data added by actions is also collected.</span></span> <span data-ttu-id="c672f-144">收集的事件資料會儲存在記憶體中，因此會有有限度的限制。</span><span class="sxs-lookup"><span data-stu-id="c672f-144">The collected event data is stored in memory, and therefore has a finite limit.</span></span> <span data-ttu-id="c672f-145">這個限制是以系統容量和活動為根據。</span><span class="sxs-lookup"><span data-stu-id="c672f-145">This limit is based on system capacity and activity.</span></span> <span data-ttu-id="c672f-146">所使用的記憶體數量將會根據可用的系統資源而定，而不會將最大記憶體數量當做參數使用。</span><span class="sxs-lookup"><span data-stu-id="c672f-146">Instead of taking the maximum amount of memory to be used as a parameter, the amount of memory used will be based on available system resources.</span></span> <span data-ttu-id="c672f-147">當無法使用這些項目時，將會卸除已經保留且未配對的事件。</span><span class="sxs-lookup"><span data-stu-id="c672f-147">When these are not available, unpaired events that have been retained will be dropped.</span></span> <span data-ttu-id="c672f-148">如果事件尚未配對且遭到卸除，則相符的事件將會以未配對事件的形式出現。</span><span class="sxs-lookup"><span data-stu-id="c672f-148">If an event has not been paired and is dropped, the matching event will appear as an unpaired event.</span></span>  
  
 <span data-ttu-id="c672f-149">配對目標會將未配對的事件序列化成 XML 格式，</span><span class="sxs-lookup"><span data-stu-id="c672f-149">The pairing target serializes unpaired events to an XML format.</span></span> <span data-ttu-id="c672f-150">這個格式不符合任何結構描述。</span><span class="sxs-lookup"><span data-stu-id="c672f-150">This format does not conform to any schema.</span></span> <span data-ttu-id="c672f-151">此格式只包含兩個元素類型。</span><span class="sxs-lookup"><span data-stu-id="c672f-151">The format only contains two element types.</span></span> <span data-ttu-id="c672f-152">**\<unpaired>** 元素是根，後面接著一個。</span><span class="sxs-lookup"><span data-stu-id="c672f-152">The **\<unpaired>** element is the root, followed by one.</span></span> <span data-ttu-id="c672f-153">**\<event>** 目前正在追蹤之每一個未配對事件的元素。</span><span class="sxs-lookup"><span data-stu-id="c672f-153">**\<event>** element for each unpaired event that is currently being tracked.</span></span> <span data-ttu-id="c672f-154">**\<event>** 元素包含一個屬性，其中包含未配對事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c672f-154">The **\<event>** element contains one attribute that contains the name of the unpaired event.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="c672f-155">將目標加入至工作階段</span><span class="sxs-lookup"><span data-stu-id="c672f-155">Adding the Target to a Session</span></span>  
 <span data-ttu-id="c672f-156">若要將配對比對目標加入至擴充事件工作階段，您必須在建立或更改事件工作階段時，加入下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="c672f-156">To add the pair matching target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.pair_matching   
```  
  
 <span data-ttu-id="c672f-157">之後，您會使用 SET 陳述式，以便定義開始和結束事件，以及要比對的動作或資料行。</span><span class="sxs-lookup"><span data-stu-id="c672f-157">You would follow this with a SET statement, to define the beginning and ending events, and which actions or columns to match.</span></span> <span data-ttu-id="c672f-158">下例顯示配對比對 sqlserver.lock_acquired 和 sqlserver.lock_released 事件的範例語法。</span><span class="sxs-lookup"><span data-stu-id="c672f-158">The following example shows sample syntax for pair matching the sqlserver.lock_acquired and sqlserver.lock_released events.</span></span>  
  
```  
   ( SET begin_event = 'sqlserver.lock_acquired',  
      begin_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
      end_event = 'sqlserver.lock_released',  
      end_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
   respond_to_memory_pressure = 1)  
```  
  
 <span data-ttu-id="c672f-159">如需詳細資訊，請參閱 [判斷哪些查詢持有鎖定](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md)。</span><span class="sxs-lookup"><span data-stu-id="c672f-159">For more information, see [Determine Which Queries Are Holding Locks](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md).</span></span>  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="c672f-160">檢閱目標輸出</span><span class="sxs-lookup"><span data-stu-id="c672f-160">Reviewing the Target Output</span></span>  
 <span data-ttu-id="c672f-161">若要檢閱配對比對目標的輸出，您可以使用下列查詢，並將 *session_name* 取代成事件工作階段的名稱。</span><span class="sxs-lookup"><span data-stu-id="c672f-161">To review the output for the pair matching target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="c672f-162">下列範例顯示配對目標輸出格式。</span><span class="sxs-lookup"><span data-stu-id="c672f-162">The following example shows the pairing target output format.</span></span>  
  
```  
<unpaired truncated = "0" matchedCount = "[matched count]" memoryPressureDroppedCount = " [lost count]">  
    <event name  = "[event name]" package = "[package]" id= "[event ID value]" version = "[event version]">  
    <data name = "[column name]">   
    <type name = "[column type]" package = "[type package]" />   
    <value>[column value]</value>  
    <text value>[text value]</text>>  
        </data>  
    </event>  
</unpaired>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c672f-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c672f-163">See Also</span></span>  
 <span data-ttu-id="c672f-164">[SQL Server 擴充的事件目標](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="c672f-164">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="c672f-165">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c672f-165">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="c672f-166">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c672f-166">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="c672f-167">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c672f-167">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
