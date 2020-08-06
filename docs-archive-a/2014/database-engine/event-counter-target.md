---
title: 事件計數器目標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f540f39176ec638cdc9236b315e306ecebfdcb1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701614"
---
# <a name="event-counter-target"></a><span data-ttu-id="be4a0-102">事件計數器目標</span><span class="sxs-lookup"><span data-stu-id="be4a0-102">Event Counter Target</span></span>
  <span data-ttu-id="be4a0-103">事件計數器目標會計算在擴充事件工作階段期間發生的所有事件。</span><span class="sxs-lookup"><span data-stu-id="be4a0-103">The event counter target counts all events that occur during an Extended Events session.</span></span> <span data-ttu-id="be4a0-104">您可以使用事件計數器目標來取得有關工作負載特性的資訊，而不會增加完整事件收集的負擔。</span><span class="sxs-lookup"><span data-stu-id="be4a0-104">By using the event counter target, you can obtain information about workload characteristics without adding the overhead of full event collection.</span></span> <span data-ttu-id="be4a0-105">此目標沒有任何可自訂的參數。</span><span class="sxs-lookup"><span data-stu-id="be4a0-105">This target has no customizable parameters.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="be4a0-106">將目標加入至工作階段</span><span class="sxs-lookup"><span data-stu-id="be4a0-106">Adding the Target to a Session</span></span>  
 <span data-ttu-id="be4a0-107">若要將事件計數器目標加入至擴充事件工作階段，您必須在建立或改變事件工作階段時，加入下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="be4a0-107">To add the event counter target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="be4a0-108">檢閱目標輸出</span><span class="sxs-lookup"><span data-stu-id="be4a0-108">Reviewing the Target Output</span></span>  
 <span data-ttu-id="be4a0-109">若要檢閱事件計數器目標的輸出，您可以使用下列查詢，並將 *session_name* 取代成事件工作階段的名稱：</span><span class="sxs-lookup"><span data-stu-id="be4a0-109">To review the output from the event counter target, you can use the following query, replacing *session_name* with the name of the event session:</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="be4a0-110">下列範例顯示事件計數器目標輸出格式。</span><span class="sxs-lookup"><span data-stu-id="be4a0-110">The following example shows the event counter target output format.</span></span>  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be4a0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be4a0-111">See Also</span></span>  
 <span data-ttu-id="be4a0-112">[SQL Server 擴充的事件目標](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="be4a0-112">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="be4a0-113">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="be4a0-113">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="be4a0-114">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="be4a0-114">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="be4a0-115">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="be4a0-115">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
