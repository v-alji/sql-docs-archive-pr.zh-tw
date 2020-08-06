---
title: 監視複寫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: rothja
ms.author: jroth
ms.openlocfilehash: df2760e4ce04c95f38ceb9dfe9fa9f79c4c467f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702810"
---
# <a name="monitoring-replication"></a><span data-ttu-id="3139c-102">監視 (複寫)</span><span class="sxs-lookup"><span data-stu-id="3139c-102">Monitoring (Replication)</span></span>
  <span data-ttu-id="3139c-103">監控複寫拓撲是部署複寫時很重要的層面。</span><span class="sxs-lookup"><span data-stu-id="3139c-103">Monitoring a replication topology is an important aspect of deploying replication.</span></span> <span data-ttu-id="3139c-104">由於已散發複寫活動，因此必須跨越所有複寫相關的電腦，追蹤活動和狀態</span><span class="sxs-lookup"><span data-stu-id="3139c-104">Because replication activity is distributed, it is essential to track activity and status across all computers involved in replication.</span></span> <span data-ttu-id="3139c-105">下列工具可用來監視複寫：</span><span class="sxs-lookup"><span data-stu-id="3139c-105">The following tools can be used to monitor replication:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)]<span data-ttu-id="3139c-106">複寫 [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] 監視器</span><span class="sxs-lookup"><span data-stu-id="3139c-106">[!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] Replication Monitor</span></span>  
  
     <span data-ttu-id="3139c-107">「複寫監視器」是最重要的複寫監視工具，可呈現所有複寫活動以發行者為焦點的檢視。</span><span class="sxs-lookup"><span data-stu-id="3139c-107">Replication Monitor is the most important tool for monitoring replication, presenting a Publisher-focused view of all replication activity.</span></span> <span data-ttu-id="3139c-108">如需詳細資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3139c-108">For more information, see [Monitor performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] <span data-ttu-id="3139c-109">[!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3139c-109">[!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]</span></span>  
  
     [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] <span data-ttu-id="3139c-110">提供「複寫監視器」的存取權。</span><span class="sxs-lookup"><span data-stu-id="3139c-110">provides access to Replication Monitor.</span></span> <span data-ttu-id="3139c-111">它也可讓您檢視下列代理程式所記錄的目前狀態和最後訊息，並可讓您啟動和停止每個代理程式：記錄讀取器代理程式、快照集代理程式、合併代理程式，以及散發代理程式。</span><span class="sxs-lookup"><span data-stu-id="3139c-111">It also allows you to view the current status and last message logged by the following agents and allows you start and stop each agent: Log Reader Agent, Snapshot Agent, Merge Agent, and Distribution Agent.</span></span> <span data-ttu-id="3139c-112">如需相關資訊，請參閱 [Monitor Replication Agents](monitor/monitor-replication-agents.md)。</span><span class="sxs-lookup"><span data-stu-id="3139c-112">For more information, see [Monitor Replication Agents](monitor/monitor-replication-agents.md).</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="3139c-113">和 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="3139c-113">and Replication Management Objects (RMO)</span></span>  
  
     <span data-ttu-id="3139c-114">兩個介面均可讓您監視「散發者」端所有類型的複寫。</span><span class="sxs-lookup"><span data-stu-id="3139c-114">Both interfaces allow you to monitor all types of replication from the Distributor.</span></span> <span data-ttu-id="3139c-115">合併式複寫還提供了監視「訂閱者」端複寫的能力。</span><span class="sxs-lookup"><span data-stu-id="3139c-115">Merge replication also provides the ability to monitor replication from the Subscriber.</span></span>  
  
-   <span data-ttu-id="3139c-116">複寫代理程式事件的警示</span><span class="sxs-lookup"><span data-stu-id="3139c-116">Alerts for replication agent events</span></span>  
  
     <span data-ttu-id="3139c-117">複寫提供了一些複寫代理程式事件的預先定義警示，必要時您還可以建立其他警示。</span><span class="sxs-lookup"><span data-stu-id="3139c-117">Replication provides a number of predefined alerts for replication agent events, and you can create additional alerts if necessary.</span></span> <span data-ttu-id="3139c-118">警示可用於觸發對事件的自動回應及 (或) 通知管理員。</span><span class="sxs-lookup"><span data-stu-id="3139c-118">Alerts can be used to trigger an automated response to an event and/or notify an administrator.</span></span> <span data-ttu-id="3139c-119">如需詳細資訊，請參閱[使用複寫代理程式事件的警示](agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="3139c-119">For more information, see [Use Alerts for Replication Agent Events](agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
-   <span data-ttu-id="3139c-120">系統監視器</span><span class="sxs-lookup"><span data-stu-id="3139c-120">System Monitor</span></span>  
  
     <span data-ttu-id="3139c-121">「系統監視器」提供了許多複寫計數器，有助於監視效能。</span><span class="sxs-lookup"><span data-stu-id="3139c-121">System Monitor can be useful for monitoring performance, providing a number of counters for replication.</span></span> <span data-ttu-id="3139c-122">如需相關資訊，請參閱 [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3139c-122">For more information, see [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3139c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3139c-123">See Also</span></span>  
 <span data-ttu-id="3139c-124">[複寫管理常見問題集](administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="3139c-124">[Replication Administration FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 [<span data-ttu-id="3139c-125">Best Practices for Replication Administration</span><span class="sxs-lookup"><span data-stu-id="3139c-125">Best Practices for Replication Administration</span></span>](administration/best-practices-for-replication-administration.md)   

  
  
