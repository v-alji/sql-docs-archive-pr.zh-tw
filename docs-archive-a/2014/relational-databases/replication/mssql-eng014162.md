---
title: MSSQL_ENG014162 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014162 error
ms.assetid: a15eef3f-219f-45d3-8286-6a864c85a723
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 78c6eb13087a7f7d5b2711af4484df7a384d7835
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606793"
---
# <a name="mssql_eng014162"></a><span data-ttu-id="71008-102">MSSQL_ENG014162</span><span class="sxs-lookup"><span data-stu-id="71008-102">MSSQL_ENG014162</span></span>
    
## <a name="message-details"></a><span data-ttu-id="71008-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="71008-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71008-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="71008-104">Product Name</span></span>|<span data-ttu-id="71008-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="71008-105">SQL Server</span></span>|  
|<span data-ttu-id="71008-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="71008-106">Event ID</span></span>|<span data-ttu-id="71008-107">14162</span><span class="sxs-lookup"><span data-stu-id="71008-107">14162</span></span>|  
|<span data-ttu-id="71008-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="71008-108">Event Source</span></span>|<span data-ttu-id="71008-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="71008-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="71008-110">元件</span><span class="sxs-lookup"><span data-stu-id="71008-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="71008-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="71008-111">Symbolic Name</span></span>||  
|<span data-ttu-id="71008-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="71008-112">Message Text</span></span>|<span data-ttu-id="71008-113">已設定針對發行集[%s]的臨界值[%s:%s]</span><span class="sxs-lookup"><span data-stu-id="71008-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="71008-114">請確定合併代理程式正在執行，而且符合預期需求。</span><span class="sxs-lookup"><span data-stu-id="71008-114">Please make sure that the merge agent is running and can match the expected requirement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="71008-115">說明</span><span class="sxs-lookup"><span data-stu-id="71008-115">Explanation</span></span>  
 <span data-ttu-id="71008-116">複寫可讓您啟用多個條件的警告。</span><span class="sxs-lookup"><span data-stu-id="71008-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="71008-117">這包括超出同步處理合併發行者與訂閱者之間變更的指定時間長度。</span><span class="sxs-lookup"><span data-stu-id="71008-117">This includes exceeding a specified length of time for synchronizing changes between a merge Publisher and Subscriber.</span></span> <span data-ttu-id="71008-118">您可以為 LAN 連接和撥號連接指定不同的時間。</span><span class="sxs-lookup"><span data-stu-id="71008-118">Different times can be specified for LAN connections and dial-up connections.</span></span>  
  
 <span data-ttu-id="71008-119">使用複寫監視器或 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)啟用警告時，您會指定決定何時觸發警告的臨界值。</span><span class="sxs-lookup"><span data-stu-id="71008-119">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="71008-120">當達到或超過臨界值時，複寫監視器中會顯示警告，而且會有事件寫入 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="71008-120">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="71008-121">達到臨界值也會觸發 SQL Server Agent 警示。</span><span class="sxs-lookup"><span data-stu-id="71008-121">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="71008-122">如需詳細資訊，請參閱[在複寫監視器中設定臨界值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)和[以程式設計方式監視複寫](monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="71008-122">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="71008-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="71008-123">User Action</span></span>  
 <span data-ttu-id="71008-124">如果訂閱超過持續時間臨界值，則必須判斷是否發生系統效能問題，或者應該調整臨界值。</span><span class="sxs-lookup"><span data-stu-id="71008-124">If a subscription exceeds a duration threshold, you must determine whether there is a performance issue with the system or whether the threshold should be adjusted.</span></span> <span data-ttu-id="71008-125">在設定複寫後，請開發效能基準線，以便決定複寫對應用程式及拓撲一般工作負載的操作方式。</span><span class="sxs-lookup"><span data-stu-id="71008-125">After you configure replication, develop a performance baseline that will let you determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="71008-126">請將同步處理持續時間包含在此基準線中，以便用於設定適當的臨界值。</span><span class="sxs-lookup"><span data-stu-id="71008-126">Include duration of synchronization in this baseline so that you can set an appropriate value for the threshold.</span></span>  
  
 <span data-ttu-id="71008-127">如果臨界值適當，但是即將超過，您就必須判斷系統的效能瓶頸何在。</span><span class="sxs-lookup"><span data-stu-id="71008-127">If the threshold value is appropriate, but it is being exceeded, you must determine where the performance bottleneck is in the system.</span></span> <span data-ttu-id="71008-128">如需有關如何監視與疑難排解複寫效能的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="71008-128">For more information about how to monitor and troubleshoot replication performance, see the following topics:</span></span>  
  
-   <span data-ttu-id="71008-129">[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md) (特別是＜檢視合併式複寫的詳細同步處理效能＞一節)</span><span class="sxs-lookup"><span data-stu-id="71008-129">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) (especially the section "Viewing Detailed Synchronization Performance for Merge Replication")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71008-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71008-130">See Also</span></span>  
 [<span data-ttu-id="71008-131">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="71008-131">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
