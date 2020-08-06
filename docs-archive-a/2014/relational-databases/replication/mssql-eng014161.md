---
title: MSSQL_ENG014161 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014161 error
ms.assetid: 4b983e76-bb77-43c5-b44b-19919d3da619
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8cf85181e444385e1a3908761ba71414b68cf3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584411"
---
# <a name="mssql_eng014161"></a><span data-ttu-id="2bb55-102">MSSQL_ENG014161</span><span class="sxs-lookup"><span data-stu-id="2bb55-102">MSSQL_ENG014161</span></span>
    
## <a name="message-details"></a><span data-ttu-id="2bb55-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="2bb55-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2bb55-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2bb55-104">Product Name</span></span>|<span data-ttu-id="2bb55-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2bb55-105">SQL Server</span></span>|  
|<span data-ttu-id="2bb55-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2bb55-106">Event ID</span></span>|<span data-ttu-id="2bb55-107">14161</span><span class="sxs-lookup"><span data-stu-id="2bb55-107">14161</span></span>|  
|<span data-ttu-id="2bb55-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2bb55-108">Event Source</span></span>|<span data-ttu-id="2bb55-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2bb55-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2bb55-110">元件</span><span class="sxs-lookup"><span data-stu-id="2bb55-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="2bb55-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2bb55-111">Symbolic Name</span></span>||  
|<span data-ttu-id="2bb55-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2bb55-112">Message Text</span></span>|<span data-ttu-id="2bb55-113">已設定針對發行集[%s]的臨界值[%s:%s]</span><span class="sxs-lookup"><span data-stu-id="2bb55-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="2bb55-114">請確定記錄讀取器和散發代理程式正在執行，而且符合延遲需求。</span><span class="sxs-lookup"><span data-stu-id="2bb55-114">Make sure that the logreader and distribution agents are running and can match the latency requirement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2bb55-115">說明</span><span class="sxs-lookup"><span data-stu-id="2bb55-115">Explanation</span></span>  
 <span data-ttu-id="2bb55-116">複寫可讓您啟用多個條件的警告。</span><span class="sxs-lookup"><span data-stu-id="2bb55-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="2bb55-117">這包括超過指定的交易式訂閱延遲。</span><span class="sxs-lookup"><span data-stu-id="2bb55-117">This includes exceeding a specified latency for transactional subscriptions.</span></span> <span data-ttu-id="2bb55-118">延遲是指，資料變更受發行者認可與對應變更受訂閱者認可之間所經過的時間。</span><span class="sxs-lookup"><span data-stu-id="2bb55-118">Latency is the period of time that elapses between a data change being committed at the Publisher and the corresponding change being committed at the Subscriber.</span></span>  
  
 <span data-ttu-id="2bb55-119">使用複寫監視器或 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)啟用警告時，您會指定決定何時觸發警告的臨界值。</span><span class="sxs-lookup"><span data-stu-id="2bb55-119">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="2bb55-120">當達到或超過臨界值時，複寫監視器中會顯示警告，而且會有事件寫入 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2bb55-120">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="2bb55-121">達到臨界值也會觸發 SQL Server Agent 警示。</span><span class="sxs-lookup"><span data-stu-id="2bb55-121">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="2bb55-122">如需詳細資訊，請參閱[在複寫監視器中設定臨界值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)和[以程式設計方式監視複寫](monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="2bb55-122">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2bb55-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2bb55-123">User Action</span></span>  
 <span data-ttu-id="2bb55-124">如果訂閱超過延遲臨界值，則必須判斷是否發生系統效能問題，或者應該調整臨界值。</span><span class="sxs-lookup"><span data-stu-id="2bb55-124">If a subscription exceeds a latency threshold, you must determine whether there is a performance issue with the system or whether the threshold should be adjusted.</span></span> <span data-ttu-id="2bb55-125">在設定複寫後，請開發效能基準線，以便決定複寫對應用程式及拓撲一般工作負載的操作方式。</span><span class="sxs-lookup"><span data-stu-id="2bb55-125">After you configure replication, develop a performance baseline that will let you determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="2bb55-126">請將延遲包含在此基準線中，以便用於設定適當的臨界值。</span><span class="sxs-lookup"><span data-stu-id="2bb55-126">Include latency in this baseline so that you can set an appropriate value for the threshold.</span></span>  
  
 <span data-ttu-id="2bb55-127">如果臨界值適當，但是即將超過，您就必須判斷系統的效能瓶頸何在。</span><span class="sxs-lookup"><span data-stu-id="2bb55-127">If the threshold value is appropriate, but it is being exceeded, you must determine where the performance bottleneck is in the system.</span></span> <span data-ttu-id="2bb55-128">如需有關如何監視與疑難排解複寫效能的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="2bb55-128">For more information about how to monitor and troubleshoot replication performance, see the following topics:</span></span>  
  
-   [<span data-ttu-id="2bb55-129">針對異動複寫測量延遲及驗證連接</span><span class="sxs-lookup"><span data-stu-id="2bb55-129">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
-   [<span data-ttu-id="2bb55-130">使用複寫監視器監視效能</span><span class="sxs-lookup"><span data-stu-id="2bb55-130">Monitor Performance with Replication Monitor</span></span>](monitor/monitor-performance-with-replication-monitor.md)  
  
## <a name="see-also"></a><span data-ttu-id="2bb55-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bb55-131">See Also</span></span>  
 [<span data-ttu-id="2bb55-132">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="2bb55-132">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
