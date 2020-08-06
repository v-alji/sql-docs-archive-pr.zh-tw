---
title: 長條圖目標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- bucketing target [SQL Server extended events]
- event bucketing target
- targets [SQL Server extended events], bucketing
ms.assetid: 2ea39141-7eb0-4c74-abf8-114c2c106a19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: acb124ef949849561a6bca0ba4016b40c1343384
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700204"
---
# <a name="histogram-target"></a><span data-ttu-id="ed286-102">長條圖目標</span><span class="sxs-lookup"><span data-stu-id="ed286-102">Histogram Target</span></span>
  <span data-ttu-id="ed286-103">長條圖目標會根據事件資料來分組特定事件類型的發生。</span><span class="sxs-lookup"><span data-stu-id="ed286-103">The histogram target groups occurrences of a specific event type based on event data.</span></span> <span data-ttu-id="ed286-104">事件的群組會根據指定的事件資料行或動作來計算。</span><span class="sxs-lookup"><span data-stu-id="ed286-104">The groupings of events are counted based on a specified event column or action.</span></span> <span data-ttu-id="ed286-105">您可以使用長條圖目標來排除效能問題。</span><span class="sxs-lookup"><span data-stu-id="ed286-105">You can use the histogram target to troubleshoot performance issues.</span></span> <span data-ttu-id="ed286-106">藉由識別哪些事件最常發生，您可以尋找「作用點」來指出效能問題的可能原因。</span><span class="sxs-lookup"><span data-stu-id="ed286-106">By identifying which events are occurring most frequently, you can find "hotspots" that indicate a potential cause of a performance problem.</span></span>  
  
 <span data-ttu-id="ed286-107">下表說明可用來設定長條圖目標的選項。</span><span class="sxs-lookup"><span data-stu-id="ed286-107">The following table describes the options that can be used to configure the histogram target.</span></span>  
  
|<span data-ttu-id="ed286-108">選項</span><span class="sxs-lookup"><span data-stu-id="ed286-108">Option</span></span>|<span data-ttu-id="ed286-109">允許的值</span><span class="sxs-lookup"><span data-stu-id="ed286-109">Allowed values</span></span>|<span data-ttu-id="ed286-110">描述</span><span class="sxs-lookup"><span data-stu-id="ed286-110">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="ed286-111">slots</span><span class="sxs-lookup"><span data-stu-id="ed286-111">slots</span></span>|<span data-ttu-id="ed286-112">任何整數值。</span><span class="sxs-lookup"><span data-stu-id="ed286-112">Any integer value.</span></span> <span data-ttu-id="ed286-113">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="ed286-113">This value is optional.</span></span>|<span data-ttu-id="ed286-114">使用者指定的值，指示要保留的群組數目上限。</span><span class="sxs-lookup"><span data-stu-id="ed286-114">A user-specified value indicating the maximum number of groupings to retain.</span></span> <span data-ttu-id="ed286-115">當到達這個值時，會忽略不屬於現有群組的新事件。</span><span class="sxs-lookup"><span data-stu-id="ed286-115">When this value is reached, new events that do not belong to the existing groups are ignored.</span></span><br /><br /> <span data-ttu-id="ed286-116">請注意，為了提升效能，插槽編號會進位到下一個 2 的乘冪。</span><span class="sxs-lookup"><span data-stu-id="ed286-116">Note that to improve performance, the slot number is rounded up to the next power of 2.</span></span>|  
|<span data-ttu-id="ed286-117">filtering_event_name</span><span class="sxs-lookup"><span data-stu-id="ed286-117">filtering_event_name</span></span>|<span data-ttu-id="ed286-118">擴充的事件工作階段中所存在的任何事件。</span><span class="sxs-lookup"><span data-stu-id="ed286-118">Any event present in the Extended Events session.</span></span> <span data-ttu-id="ed286-119">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="ed286-119">This value is optional.</span></span>|<span data-ttu-id="ed286-120">使用者指定的值，用來識別事件類別。</span><span class="sxs-lookup"><span data-stu-id="ed286-120">A user-specified value that is used to identify a class of events.</span></span> <span data-ttu-id="ed286-121">只有指定之事件的執行個體才會儲存起來，</span><span class="sxs-lookup"><span data-stu-id="ed286-121">Only instances of the specified event are bucketed.</span></span> <span data-ttu-id="ed286-122">所有其他事件則會忽略。</span><span class="sxs-lookup"><span data-stu-id="ed286-122">All other events are ignored.</span></span><br /><br /> <span data-ttu-id="ed286-123">如果您指定這個值，您必須使用 *package_name*.*event_name*格式，例如 `'sqlserver.checkpoint_end'`。</span><span class="sxs-lookup"><span data-stu-id="ed286-123">If you specify this value, you must use the format: *package_name*.*event_name*, for example `'sqlserver.checkpoint_end'`.</span></span> <span data-ttu-id="ed286-124">您可以使用下列查詢來識別封裝名稱：</span><span class="sxs-lookup"><span data-stu-id="ed286-124">You can identify the package name by using the following query:</span></span><br /><br /> <span data-ttu-id="ed286-125">選取 [p.name]、[se] event_name</span><span class="sxs-lookup"><span data-stu-id="ed286-125">SELECT p.name, se.event_name</span></span><br /><span data-ttu-id="ed286-126">從 sys. dm_xe_session_events se</span><span class="sxs-lookup"><span data-stu-id="ed286-126">FROM sys.dm_xe_session_events se</span></span><br /><span data-ttu-id="ed286-127">加入 sys.databases dm_xe_packages p</span><span class="sxs-lookup"><span data-stu-id="ed286-127">JOIN sys.dm_xe_packages p</span></span><br /><span data-ttu-id="ed286-128">在 se_event_package_guid = p. guid</span><span class="sxs-lookup"><span data-stu-id="ed286-128">ON se_event_package_guid = p.guid</span></span><br /><span data-ttu-id="ed286-129">ORDER BY p.name，se. event_name</span><span class="sxs-lookup"><span data-stu-id="ed286-129">ORDER BY p.name, se.event_name</span></span><br /><br /> <br /><br /> <span data-ttu-id="ed286-130">如果您未指定 filtering_event_name 值，source_type 必須設定為 1 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="ed286-130">If you do not specify the filtering_event_name value, source_type must be set to 1 (the default).</span></span>|  
|<span data-ttu-id="ed286-131">source_type</span><span class="sxs-lookup"><span data-stu-id="ed286-131">source_type</span></span>|<span data-ttu-id="ed286-132">值區所根據的物件類型。</span><span class="sxs-lookup"><span data-stu-id="ed286-132">The type of object that the bucket is based on.</span></span> <span data-ttu-id="ed286-133">這個值是選用的值，而且如果未指定它，它的預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="ed286-133">This value is optional and if not specified has a default value of 1.</span></span>|<span data-ttu-id="ed286-134">可以具有下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="ed286-134">Can have one of the following values:</span></span><br /><br /> <span data-ttu-id="ed286-135">0 代表事件。</span><span class="sxs-lookup"><span data-stu-id="ed286-135">0 for an event</span></span><br /><br /> <span data-ttu-id="ed286-136">1 代表動作。</span><span class="sxs-lookup"><span data-stu-id="ed286-136">1 for an action</span></span>|  
|<span data-ttu-id="ed286-137">source</span><span class="sxs-lookup"><span data-stu-id="ed286-137">source</span></span>|<span data-ttu-id="ed286-138">事件資料行或動作名稱。</span><span class="sxs-lookup"><span data-stu-id="ed286-138">Event column or action name.</span></span>|<span data-ttu-id="ed286-139">當做資料來源使用的事件資料行或動作名稱。</span><span class="sxs-lookup"><span data-stu-id="ed286-139">The event column or action name that is used as the data source.</span></span><br /><br /> <span data-ttu-id="ed286-140">當您為來源指定事件資料行時，您必須從用於 filtering_event_name 值的事件來指定資料行。</span><span class="sxs-lookup"><span data-stu-id="ed286-140">When you specify an event column for source, you must specify a column from the event that is used for the filtering_event_name value.</span></span> <span data-ttu-id="ed286-141">您可以使用下列查詢來識別可能的資料行：</span><span class="sxs-lookup"><span data-stu-id="ed286-141">You can identify the potential columns by using the following query:</span></span><br /><br /> <span data-ttu-id="ed286-142">從 sys.databases 選取 [名稱] dm_xe_object_columns</span><span class="sxs-lookup"><span data-stu-id="ed286-142">SELECT name FROM sys.dm_xe_object_columns</span></span><br /><span data-ttu-id="ed286-143">其中 object_name = ' \<eventname> '</span><span class="sxs-lookup"><span data-stu-id="ed286-143">WHERE object_name = '\<eventname>'</span></span><br /><span data-ttu-id="ed286-144">和 column_type！ = ' readonly '</span><span class="sxs-lookup"><span data-stu-id="ed286-144">AND column_type != 'readonly'</span></span><br /><br /> <span data-ttu-id="ed286-145">當您為來源指定事件資料行時，您不必在來源值中包含封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="ed286-145">When you specify an event column for source, you do not have to include the package name in the source value.</span></span><br /><br /> <span data-ttu-id="ed286-146">當您為來源指定動作名稱時，您必須在正在使用此目標的事件工作階段中，使用針對集合所設定的其中一個動作。</span><span class="sxs-lookup"><span data-stu-id="ed286-146">When you specify an action name for source, you must use one of the actions that is configured for collection in the event session for which this target is being used.</span></span> <span data-ttu-id="ed286-147">若要尋找動作名稱的可能值，您可以查詢 sys.dm_xe_sesssion_event_actions 檢視表的 action_name 資料行。</span><span class="sxs-lookup"><span data-stu-id="ed286-147">To find potential values for the action name, you can query the action_name column of the sys.dm_xe_sesssion_event_actions view.</span></span><br /><br /> <span data-ttu-id="ed286-148">如果您將動作名稱當作資料來源使用，您必須使用 *package_name*.*action_name*格式來指定來源值。</span><span class="sxs-lookup"><span data-stu-id="ed286-148">If you are using an action name as the data source, you must specify the source value by using the format: *package_name*.*action_name*.</span></span>|  
  
 <span data-ttu-id="ed286-149">下列範例將以高層級的方式說明長條圖目標如何收集資料。</span><span class="sxs-lookup"><span data-stu-id="ed286-149">The following example illustrates at a high level how the histogram target collects data.</span></span> <span data-ttu-id="ed286-150">在此範例中，您想要使用長條圖目標來計算所發生之每一個等候類型的等候次數。</span><span class="sxs-lookup"><span data-stu-id="ed286-150">In this example, you want to use the histogram target to count how many waits of each wait type occurred.</span></span> <span data-ttu-id="ed286-151">若要這樣做，當您定義長條圖目標時，您會指定下列選項：</span><span class="sxs-lookup"><span data-stu-id="ed286-151">To do this, you would specify the following options when you define the histogram target:</span></span>  
  
-   <span data-ttu-id="ed286-152">filtering_event_name = 'wait_info'</span><span class="sxs-lookup"><span data-stu-id="ed286-152">filtering_event_name = 'wait_info'</span></span>  
  
-   <span data-ttu-id="ed286-153">source = 'wait_type'</span><span class="sxs-lookup"><span data-stu-id="ed286-153">source = 'wait_type'</span></span>  
  
-   <span data-ttu-id="ed286-154">source_type = 0 (因為 wait_type 為事件資料行)</span><span class="sxs-lookup"><span data-stu-id="ed286-154">source_type = 0 (because wait_type is an event column)</span></span>  
  
 <span data-ttu-id="ed286-155">在此案例中，將會針對 wait_type 來源記錄以下資料。</span><span class="sxs-lookup"><span data-stu-id="ed286-155">In the example scenario, the following data is recorded for the wait_type source.</span></span>  
  
|<span data-ttu-id="ed286-156">篩選事件名稱</span><span class="sxs-lookup"><span data-stu-id="ed286-156">Filtering event name</span></span>|<span data-ttu-id="ed286-157">來源資料行值</span><span class="sxs-lookup"><span data-stu-id="ed286-157">Source column value</span></span>|  
|--------------------------|-------------------------|  
|<span data-ttu-id="ed286-158">wait_info</span><span class="sxs-lookup"><span data-stu-id="ed286-158">wait_info</span></span>|<span data-ttu-id="ed286-159">file_io</span><span class="sxs-lookup"><span data-stu-id="ed286-159">file_io</span></span>|  
|<span data-ttu-id="ed286-160">wait_info</span><span class="sxs-lookup"><span data-stu-id="ed286-160">wait_info</span></span>|<span data-ttu-id="ed286-161">file_io</span><span class="sxs-lookup"><span data-stu-id="ed286-161">file_io</span></span>|  
|<span data-ttu-id="ed286-162">wait_info</span><span class="sxs-lookup"><span data-stu-id="ed286-162">wait_info</span></span>|<span data-ttu-id="ed286-163">network</span><span class="sxs-lookup"><span data-stu-id="ed286-163">network</span></span>|  
|<span data-ttu-id="ed286-164">wait_info</span><span class="sxs-lookup"><span data-stu-id="ed286-164">wait_info</span></span>|<span data-ttu-id="ed286-165">network</span><span class="sxs-lookup"><span data-stu-id="ed286-165">network</span></span>|  
|<span data-ttu-id="ed286-166">wait_info</span><span class="sxs-lookup"><span data-stu-id="ed286-166">wait_info</span></span>|<span data-ttu-id="ed286-167">sleep</span><span class="sxs-lookup"><span data-stu-id="ed286-167">sleep</span></span>|  
  
 <span data-ttu-id="ed286-168">等候類型值會分成三個位置，值和位置計數如下：</span><span class="sxs-lookup"><span data-stu-id="ed286-168">The wait type values would be categorized into three slots, with the following values and slot counts:</span></span>  
  
|<span data-ttu-id="ed286-169">值</span><span class="sxs-lookup"><span data-stu-id="ed286-169">Value</span></span>|<span data-ttu-id="ed286-170">位置計數</span><span class="sxs-lookup"><span data-stu-id="ed286-170">Slot count</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="ed286-171">file_io</span><span class="sxs-lookup"><span data-stu-id="ed286-171">file_io</span></span>|<span data-ttu-id="ed286-172">2</span><span class="sxs-lookup"><span data-stu-id="ed286-172">2</span></span>|  
|<span data-ttu-id="ed286-173">network</span><span class="sxs-lookup"><span data-stu-id="ed286-173">network</span></span>|<span data-ttu-id="ed286-174">2</span><span class="sxs-lookup"><span data-stu-id="ed286-174">2</span></span>|  
|<span data-ttu-id="ed286-175">sleep</span><span class="sxs-lookup"><span data-stu-id="ed286-175">sleep</span></span>|<span data-ttu-id="ed286-176">1</span><span class="sxs-lookup"><span data-stu-id="ed286-176">1</span></span>|  
  
 <span data-ttu-id="ed286-177">長條圖目標只會保留指定之來源的事件資料。</span><span class="sxs-lookup"><span data-stu-id="ed286-177">The histogram target only retains event data for the specified source.</span></span> <span data-ttu-id="ed286-178">在某些情況下，事件資料可能會太大而無法完整保留，此時資料會遭到截斷。</span><span class="sxs-lookup"><span data-stu-id="ed286-178">In some cases the event data may be too large to retain completely, in which case the data is truncated.</span></span> <span data-ttu-id="ed286-179">當事件資料遭到截斷時，位元組數目會記錄下來並顯示為 XML 輸出。</span><span class="sxs-lookup"><span data-stu-id="ed286-179">When event data is truncated, the number of bytes is recorded and displayed as XML output.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="ed286-180">將目標加入至工作階段</span><span class="sxs-lookup"><span data-stu-id="ed286-180">Adding the Target to a Session</span></span>  
 <span data-ttu-id="ed286-181">若要將長條圖目標加入至擴充事件工作階段，您必須在建立或改變事件工作階段時，根據所需的目標類型加入下列其中一個陳述式：</span><span class="sxs-lookup"><span data-stu-id="ed286-181">To add the histogram target to an Extended Events session, you must include either of the following statements when you create or alter an event session, depending on the desired target type:</span></span>  
  
```  
ADD TARGET package0.histogram  
```  
  
 <span data-ttu-id="ed286-182">您可以使用 SET 陳述式來設定各種選項。</span><span class="sxs-lookup"><span data-stu-id="ed286-182">You can use the SET statement to set the various options.</span></span> <span data-ttu-id="ed286-183">下列範例將示範如何加入長條圖目標，以便收集 sqlserver.checkpoint_end 事件的資料。</span><span class="sxs-lookup"><span data-stu-id="ed286-183">The following example shows the addition of the histogram target, where data for the sqlserver.checkpoint_end event is collected.</span></span>  
  
```  
ADD TARGET package0.histogram  
(SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id')  
```  
  
 <span data-ttu-id="ed286-184">如需詳細資訊，請參閱 [尋找持有最多鎖定的物件](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md)和 [使用擴充事件監視系統活動](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)。</span><span class="sxs-lookup"><span data-stu-id="ed286-184">For more information, see [Find the Objects That Have the Most Locks Taken on Them](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md), and [Monitor System Activity Using Extended Events](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).</span></span>  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="ed286-185">檢閱目標輸出</span><span class="sxs-lookup"><span data-stu-id="ed286-185">Reviewing the Target Output</span></span>  
 <span data-ttu-id="ed286-186">長條圖目標會將資料序列化成 XML 格式的呼叫程式或程序。</span><span class="sxs-lookup"><span data-stu-id="ed286-186">The histogram target serializes data to a calling program or procedure in XML format.</span></span> <span data-ttu-id="ed286-187">目標輸出不符合任何結構描述。</span><span class="sxs-lookup"><span data-stu-id="ed286-187">The target output does not conform to any schema.</span></span>  
  
 <span data-ttu-id="ed286-188">若要檢閱長條圖目標的輸出，您可以使用下列查詢，並將 *session_name* 取代成事件工作階段的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed286-188">To review the output from the histogram target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="ed286-189">下列範例說明長條圖目標輸出格式。</span><span class="sxs-lookup"><span data-stu-id="ed286-189">The following example illustrates histogram target output format.</span></span>  
  
```  
<Slots truncated = "0" buckets=[count]>  
    <Slot count=[count] trunc=[truncated bytes]>  
        <value>  
        </value>  
    </Slot>  
</Slots>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed286-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed286-190">See Also</span></span>  
 <span data-ttu-id="ed286-191">[SQL Server 擴充的事件目標](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="ed286-191">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="ed286-192">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed286-192">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="ed286-193">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed286-193">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="ed286-194">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ed286-194">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
