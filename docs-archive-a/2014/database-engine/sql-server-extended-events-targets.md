---
title: SQL Server 擴充事件目標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 010b7cc29543f266b77aaf180c50173ef9f70346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585556"
---
# <a name="sql-server-extended-events-targets"></a><span data-ttu-id="3c82d-102">SQL Server Extended Events Targets</span><span class="sxs-lookup"><span data-stu-id="3c82d-102">SQL Server Extended Events Targets</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="3c82d-103">擴充的事件目標是事件取用者。</span><span class="sxs-lookup"><span data-stu-id="3c82d-103">Extended Events targets are event consumers.</span></span> <span data-ttu-id="3c82d-104">目標可以寫入至檔案、在記憶體緩衝區中儲存事件資料，或彙總事件資料。</span><span class="sxs-lookup"><span data-stu-id="3c82d-104">Targets can write to a file, store event data in a memory buffer, or aggregate event data.</span></span> <span data-ttu-id="3c82d-105">目標也能夠同步或非同步處理資料。</span><span class="sxs-lookup"><span data-stu-id="3c82d-105">Targets can process data synchronously or asynchronously.</span></span>  
  
 <span data-ttu-id="3c82d-106">擴充的事件設計可保證目標一定會收到事件一次，而且每個工作階段只會收到一次。</span><span class="sxs-lookup"><span data-stu-id="3c82d-106">The Extended Events design ensures that targets are guaranteed to receive events once and only once per session.</span></span>  
  
 <span data-ttu-id="3c82d-107">擴充的事件會提供下列幾個目標，您可將其用於擴充的事件工作階段：</span><span class="sxs-lookup"><span data-stu-id="3c82d-107">Extended Events provide the following targets that you can use for an Extended Events session:</span></span>  
  
-   [<span data-ttu-id="3c82d-108">事件計數器</span><span class="sxs-lookup"><span data-stu-id="3c82d-108">Event counter</span></span>](../../2014/database-engine/event-counter-target.md)  
  
     <span data-ttu-id="3c82d-109">計算所有指定的事件於擴充的事件工作階段期間發生的數目。</span><span class="sxs-lookup"><span data-stu-id="3c82d-109">Counts all specified events that occur during an Extended Events session.</span></span> <span data-ttu-id="3c82d-110">用於取得有關工作負載特性的資訊，而不會增加完整事件收集的負擔。</span><span class="sxs-lookup"><span data-stu-id="3c82d-110">Use to obtain information about workload characteristics without adding the overhead of full event collection.</span></span> <span data-ttu-id="3c82d-111">這是同步目標。</span><span class="sxs-lookup"><span data-stu-id="3c82d-111">This is a synchronous target.</span></span>  
  
-   [<span data-ttu-id="3c82d-112">事件檔案</span><span class="sxs-lookup"><span data-stu-id="3c82d-112">Event file</span></span>](../../2014/database-engine/event-file-target.md)  
  
     <span data-ttu-id="3c82d-113">用於將完整記憶體緩衝區的事件工作階段輸出寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="3c82d-113">Use to write event session output from complete memory buffers to disk.</span></span> <span data-ttu-id="3c82d-114">這是非同步目標。</span><span class="sxs-lookup"><span data-stu-id="3c82d-114">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="3c82d-115">事件配對</span><span class="sxs-lookup"><span data-stu-id="3c82d-115">Event pairing</span></span>](../../2014/database-engine/event-pairing-target.md)  
  
     <span data-ttu-id="3c82d-116">許多種類的事件都是以成對的形式發生，例如鎖定取得和鎖定釋放。</span><span class="sxs-lookup"><span data-stu-id="3c82d-116">Many kinds of events occur in pairs, such as lock acquires and lock releases.</span></span> <span data-ttu-id="3c82d-117">用於判斷指定之配對事件不會發生在相符集合中的時機。</span><span class="sxs-lookup"><span data-stu-id="3c82d-117">Use to determine when a specified paired event does not occur in a matched set.</span></span> <span data-ttu-id="3c82d-118">這是非同步目標。</span><span class="sxs-lookup"><span data-stu-id="3c82d-118">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="3c82d-119">Windows 事件追蹤 (ETW)</span><span class="sxs-lookup"><span data-stu-id="3c82d-119">Event Tracing for Windows (ETW)</span></span>](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     <span data-ttu-id="3c82d-120">用於建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 事件與 Windows 作業系統或應用程式事件資料的關聯。</span><span class="sxs-lookup"><span data-stu-id="3c82d-120">Use to correlate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] events with Windows operating system or application event data.</span></span> <span data-ttu-id="3c82d-121">這是同步目標。</span><span class="sxs-lookup"><span data-stu-id="3c82d-121">This is a synchronous target.</span></span>  
  
-   [<span data-ttu-id="3c82d-122">長條圖</span><span class="sxs-lookup"><span data-stu-id="3c82d-122">Histogram</span></span>](../../2014/database-engine/histogram-target.md)  
  
     <span data-ttu-id="3c82d-123">用於根據指定的事件資料行或動作，計算指定之事件的發生次數。</span><span class="sxs-lookup"><span data-stu-id="3c82d-123">Use to count the number of times that a specified event occurs, based on a specified event column or action.</span></span> <span data-ttu-id="3c82d-124">這是非同步目標。</span><span class="sxs-lookup"><span data-stu-id="3c82d-124">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="3c82d-125">信號緩衝區</span><span class="sxs-lookup"><span data-stu-id="3c82d-125">Ring buffer</span></span>](../../2014/database-engine/ring-buffer-target.md)  
  
     <span data-ttu-id="3c82d-126">用於根據先進先出 (FIFO) 規則或每一個事件的 FIFO 規則，將事件資料存放於記憶體。</span><span class="sxs-lookup"><span data-stu-id="3c82d-126">Use to hold the event data in memory on a first-in first-out (FIFO) basis, or on a per-event FIFO basis.</span></span> <span data-ttu-id="3c82d-127">這是非同步目標。</span><span class="sxs-lookup"><span data-stu-id="3c82d-127">This is an asynchronous target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c82d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c82d-128">See Also</span></span>  
 <span data-ttu-id="3c82d-129">[擴充事件](../relational-databases/extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="3c82d-129">[Extended Events](../relational-databases/extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="3c82d-130">[SQL Server 擴充的事件封裝](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span><span class="sxs-lookup"><span data-stu-id="3c82d-130">[SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span></span>  
 <span data-ttu-id="3c82d-131">[SQL Server 擴充事件會話](../relational-databases/extended-events/sql-server-extended-events-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="3c82d-131">[SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md) </span></span>  
 [<span data-ttu-id="3c82d-132">SQL Server 擴充的事件引擎</span><span class="sxs-lookup"><span data-stu-id="3c82d-132">SQL Server Extended Events Engine</span></span>](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
