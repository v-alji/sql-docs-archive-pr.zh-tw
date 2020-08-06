---
title: SQL Server 的 Broker Activation 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4048c2baecaeb4bde7a1e215a15e8c51a60a01bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699520"
---
# <a name="sql-server-broker-activation-object"></a><span data-ttu-id="74776-102">SQL Server 的 Broker Activation 物件</span><span class="sxs-lookup"><span data-stu-id="74776-102">SQL Server, Broker Activation Object</span></span>
  <span data-ttu-id="74776-103">**SQLServer:BrokerActivation** 效能物件包含效能計數器，可報告預存程序啟用的資訊。</span><span class="sxs-lookup"><span data-stu-id="74776-103">The **SQLServer:BrokerActivation** performance object contains performance counters that report information on stored procedure activation.</span></span> <span data-ttu-id="74776-104">下表列出這個物件包含的計數器。</span><span class="sxs-lookup"><span data-stu-id="74776-104">The table below lists the counters that this object contains.</span></span>  
  
|<span data-ttu-id="74776-105">SQL Server Broker 啟用計數器</span><span class="sxs-lookup"><span data-stu-id="74776-105">SQL Server Broker Activation counters</span></span>|<span data-ttu-id="74776-106">描述</span><span class="sxs-lookup"><span data-stu-id="74776-106">Description</span></span>|  
|-------------------------------------------|-----------------|  
|<span data-ttu-id="74776-107">**叫用的預存程序/秒**</span><span class="sxs-lookup"><span data-stu-id="74776-107">**Stored Procedures Invoked/sec**</span></span>|<span data-ttu-id="74776-108">此計數器會報告在執行個體中所有佇列監視器每秒所叫用的啟用預存程序總數。</span><span class="sxs-lookup"><span data-stu-id="74776-108">This counter reports the total number of activation stored procedures invoked by all queue monitors in the instance per second.</span></span>|  
|<span data-ttu-id="74776-109">**所達到的工作限制**</span><span class="sxs-lookup"><span data-stu-id="74776-109">**Task Limit Reached**</span></span>|<span data-ttu-id="74776-110">此計數器會報告佇列監視器已經啟動新工作的總次數，但如果已經執行佇列工作的最大數目就不會報告。</span><span class="sxs-lookup"><span data-stu-id="74776-110">This counter reports the total number of times that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.</span></span>|  
|<span data-ttu-id="74776-111">**所達到的工作限制/秒**</span><span class="sxs-lookup"><span data-stu-id="74776-111">**Task Limit Reached/sec**</span></span>|<span data-ttu-id="74776-112">此計數器會報告每秒佇列監視器已經啟動新工作的次數，但如果已經為佇列執行工作最大的數目就不會報告。</span><span class="sxs-lookup"><span data-stu-id="74776-112">This counter reports the number of times per second that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.</span></span>|  
|<span data-ttu-id="74776-113">**已中止的工作/秒**</span><span class="sxs-lookup"><span data-stu-id="74776-113">**Tasks Aborted/sec**</span></span>|<span data-ttu-id="74776-114">此計數器會報告啟用預存程序工作，因錯誤而結束或因無法接收訊息而由佇列監視器中止的數目。</span><span class="sxs-lookup"><span data-stu-id="74776-114">This counter reports the number of activation stored procedure tasks that end with an error, or are aborted by a queue monitor for failing to receive messages.</span></span>|  
|<span data-ttu-id="74776-115">**工作執行**</span><span class="sxs-lookup"><span data-stu-id="74776-115">**Tasks Running**</span></span>|<span data-ttu-id="74776-116">此計數器會報告目前正在執行的啟用預存程序的數目。</span><span class="sxs-lookup"><span data-stu-id="74776-116">This counter reports the number of activation stored procedures that are currently running.</span></span>|  
|<span data-ttu-id="74776-117">**已啟動的工作/秒**</span><span class="sxs-lookup"><span data-stu-id="74776-117">**Tasks Started/sec**</span></span>|<span data-ttu-id="74776-118">此計數器會報告在執行個體中所有佇列監視器每秒所啟動的啟用預存程序數目。</span><span class="sxs-lookup"><span data-stu-id="74776-118">This counter reports the number of activation stored procedures started per second by all queue monitors in the instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74776-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74776-119">See Also</span></span>  
 <span data-ttu-id="74776-120">[sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="74776-120">[sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql) </span></span>  
 <span data-ttu-id="74776-121">[sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="74776-121">[sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql) </span></span>  
 [<span data-ttu-id="74776-122">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="74776-122">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
