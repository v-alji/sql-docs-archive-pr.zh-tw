---
title: 信號緩衝區目標 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 186e847bb9f9b621543119c25510dc5d6107e274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599157"
---
# <a name="ring-buffer-target"></a><span data-ttu-id="6e7aa-102">環緩衝區目標</span><span class="sxs-lookup"><span data-stu-id="6e7aa-102">Ring Buffer Target</span></span>
  <span data-ttu-id="6e7aa-103">信號緩衝區目標會短暫地將事件資料保留在記憶體中，</span><span class="sxs-lookup"><span data-stu-id="6e7aa-103">The ring buffer target briefly holds event data in memory.</span></span> <span data-ttu-id="6e7aa-104">此目標可以在兩個模式的其中一個之下管理事件。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-104">This target can manage events in one of two modes.</span></span>  
  
-   <span data-ttu-id="6e7aa-105">第一個模式是嚴格的先進先出 (FIFO)，當使用配置給目標的所有記憶體時，將會捨棄最舊的事件。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-105">The first mode is strict first-in first-out (FIFO), where the oldest event is discarded when all the memory allocated to the target is used.</span></span> <span data-ttu-id="6e7aa-106">在此模式中 (預設值)，occurrence_number 選項設定為 0。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-106">In this mode (the default), the occurrence_number option is set to 0.</span></span>  
  
-   <span data-ttu-id="6e7aa-107">第二個模式是依事件的 FIFO，將會保留每一個類型之事件的指定數目。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-107">The second mode is per-event FIFO, where a specified number of events of each type is kept.</span></span> <span data-ttu-id="6e7aa-108">在此模式中，當使用配置給目標的所有記憶體時，會捨棄每一個類型的最舊事件。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-108">In this mode, the oldest events of each type are discarded when all the memory allocated to the target is used.</span></span> <span data-ttu-id="6e7aa-109">您可以設定 occurrence_number 選項，以指定要保留之每一個類型的事件數目。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-109">You can configure the occurrence_number option to specify the number of events of each type to keep.</span></span>  
  
 <span data-ttu-id="6e7aa-110">下表說明用來設定信號緩衝區目標的可用選項。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-110">The following table describes the available options for configuring the ring buffer target.</span></span>  
  
|<span data-ttu-id="6e7aa-111">選項</span><span class="sxs-lookup"><span data-stu-id="6e7aa-111">Option</span></span>|<span data-ttu-id="6e7aa-112">允許的值</span><span class="sxs-lookup"><span data-stu-id="6e7aa-112">Allowed values</span></span>|<span data-ttu-id="6e7aa-113">描述</span><span class="sxs-lookup"><span data-stu-id="6e7aa-113">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="6e7aa-114">max_memory</span><span class="sxs-lookup"><span data-stu-id="6e7aa-114">max_memory</span></span>|<span data-ttu-id="6e7aa-115">任何32位整數。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-115">Any 32-bit integer.</span></span> <span data-ttu-id="6e7aa-116">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-116">This value is optional.</span></span>|<span data-ttu-id="6e7aa-117">要使用的最大記憶體數量 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-117">The maximum amount of memory in kilobytes (KB) to use.</span></span> <span data-ttu-id="6e7aa-118">根據先達到的限制，卸除現有事件：max_event_limit 或 max_memory。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-118">Existing events are dropped based on the limit that is first reached: max_event_limit or max_memory.</span></span> <span data-ttu-id="6e7aa-119">最大值為 4194303 KB。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-119">The maximum value is 4194303 KB.</span></span> <span data-ttu-id="6e7aa-120">將信號緩衝區大小設定為 GB 範圍的限制之前應謹慎考慮，因為它可能會影響中的其他記憶體取用者 SQL Server</span><span class="sxs-lookup"><span data-stu-id="6e7aa-120">A careful consideration should be made before setting the ring buffer size to limits in the GB range as it may impact other memory consumers in SQL Server</span></span>|  
|<span data-ttu-id="6e7aa-121">max_event_limit</span><span class="sxs-lookup"><span data-stu-id="6e7aa-121">max_event_limit</span></span>|<span data-ttu-id="6e7aa-122">任何32位整數。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-122">Any 32-bit integer.</span></span> <span data-ttu-id="6e7aa-123">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-123">This value is optional.</span></span>|<span data-ttu-id="6e7aa-124">保留在 ring_buffer 中的最大事件數目。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-124">The maximum number of events kept in the ring_buffer.</span></span> <span data-ttu-id="6e7aa-125">根據先達到的限制，卸除現有事件：max_event_limit 或 max_memory。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-125">Existing events are dropped based on the limit that is first reached: max_event_limit or max_memory.</span></span> <span data-ttu-id="6e7aa-126">預設值 = 1000。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-126">Default = 1000.</span></span>|  
|<span data-ttu-id="6e7aa-127">occurrence_number</span><span class="sxs-lookup"><span data-stu-id="6e7aa-127">occurrence_number</span></span>|<span data-ttu-id="6e7aa-128">下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="6e7aa-128">One of the following values:</span></span><br /><br /> <span data-ttu-id="6e7aa-129">0 (預設值) = 當使用配置給目標的所有記憶體時，將會捨棄最舊的事件。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-129">0 (the default) = Oldest event is discarded when all the memory allocated to the target is used.</span></span><br /><br /> <span data-ttu-id="6e7aa-130">任何32位整數 = 要在每個事件 FIFO 之後捨棄之每個類型的事件數目。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-130">Any 32-bit integer = The number of events of each type to keep before being discarded on a per-event FIFO basis.</span></span><br /><br /> <br /><br /> <span data-ttu-id="6e7aa-131">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-131">This value is optional.</span></span>|<span data-ttu-id="6e7aa-132">要使用的 FIFO 模式，如果設定為大於 0 的值，則為要保留在緩衝區內之每一個類型的慣用事件數目。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-132">The FIFO mode to use, and, if set to a value greater than 0, the preferred number of events of each type to keep in the buffer.</span></span>|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="6e7aa-133">將目標加入至工作階段</span><span class="sxs-lookup"><span data-stu-id="6e7aa-133">Adding the Target to a Session</span></span>  
 <span data-ttu-id="6e7aa-134">若要將信號緩衝區目標加入至擴充事件工作階段，您必須在建立或更改事件工作階段時，加入下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="6e7aa-134">To add the ring buffer target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="6e7aa-135">檢閱目標輸出</span><span class="sxs-lookup"><span data-stu-id="6e7aa-135">Reviewing the Target Output</span></span>  
 <span data-ttu-id="6e7aa-136">若要檢閱信號緩衝區目標的輸出，您可以使用下列查詢，並將 *session_name* 取代成事件工作階段的名稱。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-136">To review the output from the ring buffer target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="6e7aa-137">下列範例顯示信號緩衝區目標輸出格式。</span><span class="sxs-lookup"><span data-stu-id="6e7aa-137">The following example shows the ring buffer target output format.</span></span>  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a><span data-ttu-id="6e7aa-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e7aa-138">See Also</span></span>

- [<span data-ttu-id="6e7aa-139">SQL Server 擴充的事件目標</span><span class="sxs-lookup"><span data-stu-id="6e7aa-139">SQL Server Extended Events Targets</span></span>](../../2014/database-engine/sql-server-extended-events-targets.md)
- [<span data-ttu-id="6e7aa-140">sys.dm_xe_session_targets &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6e7aa-140">sys.dm_xe_session_targets &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [<span data-ttu-id="6e7aa-141">CREATE EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6e7aa-141">CREATE EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [<span data-ttu-id="6e7aa-142">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6e7aa-142">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

