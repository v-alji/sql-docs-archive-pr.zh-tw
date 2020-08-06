---
title: 啟動及停止複寫代理程式 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40e329e0f04e8a54a2d5a40c30aff418da2cd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585894"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a><span data-ttu-id="7e7b8-102">啟動及停止複寫代理程式 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7e7b8-102">Start and Stop a Replication Agent (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7e7b8-103">從 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 [作業] 資料夾和 [複寫] 資料夾，以及從複寫監視器啟動及停止代理程式。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-103">Start and stop agents from the **Jobs** folder and the **Replication** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from Replication Monitor.</span></span> <span data-ttu-id="7e7b8-104">啟動和停止下列代理程式和作業：</span><span class="sxs-lookup"><span data-stu-id="7e7b8-104">Start and stop the following agents and jobs:</span></span>  
  
-   <span data-ttu-id="7e7b8-105">所有發行集所使用的快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-105">The Snapshot Agent, which is used by all publications.</span></span>  
  
-   <span data-ttu-id="7e7b8-106">所有交易式發行集所使用的記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-106">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
-   <span data-ttu-id="7e7b8-107">針對佇列更新訂閱啟用之交易式發行集所使用的佇列讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-107">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="7e7b8-108">散發代理程式，同步處理交易式和快照式發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-108">The Distribution Agent, which synchronizes subscriptions to transactional and snapshot publications.</span></span>  
  
-   <span data-ttu-id="7e7b8-109">合併代理程式，同步處理合併式發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-109">The Merge Agent, which synchronizes subscriptions to merge publications.</span></span>  
  
-   <span data-ttu-id="7e7b8-110">複寫維護作業。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-110">Replication maintenance jobs.</span></span>  
  
 <span data-ttu-id="7e7b8-111">如需啟動合併代理程式和散發代理程式的詳細資訊，請參閱[同步處理發送訂閱](../synchronize-a-push-subscription.md)和[同步處理提取訂閱](../synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-111">For more information about starting the Merge Agent and the Distribution Agent, see [Synchronize a Push Subscription](../synchronize-a-push-subscription.md) and [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).</span></span> <span data-ttu-id="7e7b8-112">如需維護作業的詳細資訊，請參閱[執行複寫維護作業 &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-112">For more information about maintenance jobs, see [Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md).</span></span>  
  
 <span data-ttu-id="7e7b8-113">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-113">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a><span data-ttu-id="7e7b8-114">若要從 Management Studio 啟動和停止快照集代理程式或記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="7e7b8-114">To start and stop a Snapshot Agent or Log Reader Agent from Management Studio</span></span>  
  
1.  <span data-ttu-id="7e7b8-115">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的「發行者」，然後展開伺服器節點和 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node and the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="7e7b8-116">展開 **[本機發行集]** 資料夾，然後以滑鼠右鍵按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-116">Expand the **Local Publications** folder, and then right-click a publication.</span></span>  
  
3.  <span data-ttu-id="7e7b8-117">按一下 **[檢視快照集代理程式的狀態]** 或 **[檢視記錄讀取器代理程式的狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-117">Click **View Snapshot Agent Status** or **View Log Reader Agent Status**.</span></span>  
  
4.  <span data-ttu-id="7e7b8-118">按一下 **[啟動]** 或 **[停止]** 。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-118">Click **Start** or **Stop**.</span></span>  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a><span data-ttu-id="7e7b8-119">若要從 Management Studio 啟動和停止「佇列讀取器代理程式」</span><span class="sxs-lookup"><span data-stu-id="7e7b8-119">To start and stop a Queue Reader Agent from Management Studio</span></span>  
  
1.  <span data-ttu-id="7e7b8-120">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的散發者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-120">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="7e7b8-121">展開 **[SQL Server Agent]** 資料夾，然後展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-121">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="7e7b8-122">以滑鼠右鍵按一下代理程式的作業，再按一下 **[啟動作業]** 或 **[停止作業]** 。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-122">Right-click the job for the agent, and then click **Start Job** or **Stop Job**.</span></span> <span data-ttu-id="7e7b8-123">佇列讀取器代理程式的作業名稱格式為 **[\<Distributor>].\<integer>** 。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-123">The name of the job for the Queue Reader Agent is in the form **[\<Distributor>].\<integer>**.</span></span>  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a><span data-ttu-id="7e7b8-124">若要從「複寫監視器」啟動和停止「快照集代理程式」、「記錄讀取器代理程式」或「佇列讀取器代理程式」</span><span class="sxs-lookup"><span data-stu-id="7e7b8-124">To start and stop a Snapshot Agent, Log Reader Agent, or Queue Reader Agent from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="7e7b8-125">在左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-125">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="7e7b8-126">按一下 **[代理程式]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-126">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="7e7b8-127">以滑鼠右鍵按一下代理程式，然後按一下 **[啟動代理程式]** 或 **[停止代理程式]** 。</span><span class="sxs-lookup"><span data-stu-id="7e7b8-127">Right-click an agent, and then click **Start Agent** or **Stop Agent**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7b8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e7b8-128">See Also</span></span>  
 <span data-ttu-id="7e7b8-129">[監視複寫](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="7e7b8-129">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 <span data-ttu-id="7e7b8-130">[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="7e7b8-130">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) </span></span>  
 [<span data-ttu-id="7e7b8-131">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="7e7b8-131">Replication Agents Overview</span></span>](replication-agents-overview.md)  
  
  
