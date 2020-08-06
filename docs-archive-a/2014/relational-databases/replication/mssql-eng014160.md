---
title: MSSQL_ENG014160 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3351567a31a0a0384ab8957073ab0457ef0ea7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585301"
---
# <a name="mssql_eng014160"></a><span data-ttu-id="cf07d-102">MSSQL_ENG014160</span><span class="sxs-lookup"><span data-stu-id="cf07d-102">MSSQL_ENG014160</span></span>
    
## <a name="message-details"></a><span data-ttu-id="cf07d-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="cf07d-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf07d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cf07d-104">Product Name</span></span>|<span data-ttu-id="cf07d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cf07d-105">SQL Server</span></span>|  
|<span data-ttu-id="cf07d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cf07d-106">Event ID</span></span>|<span data-ttu-id="cf07d-107">14160</span><span class="sxs-lookup"><span data-stu-id="cf07d-107">14160</span></span>|  
|<span data-ttu-id="cf07d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cf07d-108">Event Source</span></span>|<span data-ttu-id="cf07d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cf07d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cf07d-110">元件</span><span class="sxs-lookup"><span data-stu-id="cf07d-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="cf07d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cf07d-111">Symbolic Name</span></span>||  
|<span data-ttu-id="cf07d-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cf07d-112">Message Text</span></span>|<span data-ttu-id="cf07d-113">已設定針對發行集[%s]的臨界值[%s:%s]</span><span class="sxs-lookup"><span data-stu-id="cf07d-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="cf07d-114">此發行集的一個或多個訂閱已經到期。</span><span class="sxs-lookup"><span data-stu-id="cf07d-114">One or more subscriptions to this publication have expired.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf07d-115">說明</span><span class="sxs-lookup"><span data-stu-id="cf07d-115">Explanation</span></span>  
 <span data-ttu-id="cf07d-116">複寫可讓您啟用多個條件的警告。</span><span class="sxs-lookup"><span data-stu-id="cf07d-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="cf07d-117">這包括訂閱即將過期。</span><span class="sxs-lookup"><span data-stu-id="cf07d-117">This includes imminent subscription expiration.</span></span> <span data-ttu-id="cf07d-118">如果訂閱在指定 *「保留期限」* 內未執行同步處理，則會使訂閱過期。</span><span class="sxs-lookup"><span data-stu-id="cf07d-118">Subscriptions can expire if they are not synchronized within a specified *retention period*.</span></span> <span data-ttu-id="cf07d-119">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="cf07d-119">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="cf07d-120">使用複寫監視器或 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)啟用警告時，您會指定決定何時觸發警告的臨界值。</span><span class="sxs-lookup"><span data-stu-id="cf07d-120">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="cf07d-121">當達到或超過臨界值時，複寫監視器中會顯示警告，而且會有事件寫入 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="cf07d-121">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="cf07d-122">達到臨界值也會觸發 SQL Server Agent 警示。</span><span class="sxs-lookup"><span data-stu-id="cf07d-122">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="cf07d-123">如需詳細資訊，請參閱[在複寫監視器中設定臨界值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)和[以程式設計方式監視複寫](monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="cf07d-123">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf07d-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cf07d-124">User Action</span></span>  
 <span data-ttu-id="cf07d-125">此問題的解決方案需視引發警告的原因而定：</span><span class="sxs-lookup"><span data-stu-id="cf07d-125">The resolution for this issue depends on the reason the warning was raised:</span></span>  
  
-   <span data-ttu-id="cf07d-126">如果已超過臨界值，但是訂閱尚未過期，請同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="cf07d-126">If the threshold has been exceeded, but the subscription has not yet expired, synchronize the subscription.</span></span> <span data-ttu-id="cf07d-127">如需詳細資訊，請參閱 [同步處理資料](synchronize-data.md)。</span><span class="sxs-lookup"><span data-stu-id="cf07d-127">For more information, see [Synchronize Data](synchronize-data.md).</span></span>  
  
-   <span data-ttu-id="cf07d-128">如果代理程式已經在執行，但未正確複寫變更，可能會導致訂閱過期。</span><span class="sxs-lookup"><span data-stu-id="cf07d-128">If the agent has been running, but has not been replicating changes properly, this can cause the subscription to expire.</span></span> <span data-ttu-id="cf07d-129">進行異動複寫時，請確認散發代理程式和記錄讀取器代理程式正在執行。</span><span class="sxs-lookup"><span data-stu-id="cf07d-129">For transactional replication, make sure that the Distribution Agent and Log Reader Agent are running.</span></span> <span data-ttu-id="cf07d-130">進行合併式複寫時，請確認合併代理程式正在執行。</span><span class="sxs-lookup"><span data-stu-id="cf07d-130">For merge replication, make sure the Merge Agent is running.</span></span> <span data-ttu-id="cf07d-131">如需如何啟動這些代理程式的詳細資訊，請參閱[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 與[複寫代理程式可執行檔概念](concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="cf07d-131">For information about how to start these agents, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="cf07d-132">如果訂閱已過期，則必須重新初始化，或是卸除後再重新建立，需視訂閱類型及已過期時間的長短而定。</span><span class="sxs-lookup"><span data-stu-id="cf07d-132">If the subscription has expired, it must either be reinitialized or dropped and re-created, depending on the type of subscription and how long it has been expired.</span></span> <span data-ttu-id="cf07d-133">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="cf07d-133">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf07d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf07d-134">See Also</span></span>  
 [<span data-ttu-id="cf07d-135">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="cf07d-135">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
