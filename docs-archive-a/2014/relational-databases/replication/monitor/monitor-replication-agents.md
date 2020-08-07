---
title: 監視複寫代理程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], agents
- Log Reader Agent, monitoring
- Replication Monitor, agents
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- agents [SQL Server replication], monitoring
- Distribution Agent, monitoring
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: baa22ef9e9f7c4621f76838e82c309d17f1e12a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593939"
---
# <a name="monitor-replication-agents"></a><span data-ttu-id="5344c-102">監視複寫代理程式</span><span class="sxs-lookup"><span data-stu-id="5344c-102">Monitor Replication Agents</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="5344c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫監視器可全面檢視複寫活動，但也可以直接尋找特定代理程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="5344c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor provides a systemic view of replication activity, but also makes it straightforward to find information on a specific agent.</span></span> <span data-ttu-id="5344c-104">下列清單包含每個代理程式、可以在複寫監視器上找到的索引標籤，以及到說明如何存取這些索引標籤之主題的連結：</span><span class="sxs-lookup"><span data-stu-id="5344c-104">The following list includes each agent, the tabs in the Replication Monitor on which it can be found, and a link to a topic that explains how to access these tabs:</span></span>  
  
-   <span data-ttu-id="5344c-105">下列代理程式與複寫監視器中的發行集相關聯：</span><span class="sxs-lookup"><span data-stu-id="5344c-105">The following agents are associated with publications in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="5344c-106">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="5344c-106">Snapshot Agent</span></span>  
  
    -   <span data-ttu-id="5344c-107">記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="5344c-107">Log Reader Agent</span></span>  
  
    -   <span data-ttu-id="5344c-108">佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="5344c-108">Queue Reader Agent</span></span>  
  
     <span data-ttu-id="5344c-109">透過下列索引標籤，可存取與這些代理程式建立關聯的資訊和工作：[代理程式] (適用於每個「發行者」和發行集) 和 [警告] (適用於每個發行集)。</span><span class="sxs-lookup"><span data-stu-id="5344c-109">Access information and tasks associated with these agents through the following tabs: **Agents** (available for each Publisher and publication) and **Warnings** (available for each publication).</span></span> <span data-ttu-id="5344c-110">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="5344c-110">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="5344c-111">下列代理程式與複寫監視器中的訂閱相關聯：</span><span class="sxs-lookup"><span data-stu-id="5344c-111">The following agents are associated with subscriptions in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="5344c-112">散發代理程式</span><span class="sxs-lookup"><span data-stu-id="5344c-112">Distribution Agent</span></span>  
  
    -   <span data-ttu-id="5344c-113">合併代理程式</span><span class="sxs-lookup"><span data-stu-id="5344c-113">Merge Agent</span></span>  
  
     <span data-ttu-id="5344c-114">透過下列索引標籤，可存取與這些代理程式建立關聯的資訊和工作：[訂閱監看清單] (適用於每個「發行者」) 或 [所有訂閱] 索引標籤 (適用於每個發行集)。</span><span class="sxs-lookup"><span data-stu-id="5344c-114">Access information and tasks associated with these agents through the following tabs: **Subscription Watch List** (available for each Publisher) or the **All Subscriptions** tab (available for each publication).</span></span> <span data-ttu-id="5344c-115">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="5344c-115">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="using-sql-server-management-studio-to-monitor-replication-agents"></a><span data-ttu-id="5344c-116">使用 SQL Server Management Studio 監視複寫代理程式</span><span class="sxs-lookup"><span data-stu-id="5344c-116">Using SQL Server Management Studio to Monitor Replication Agents</span></span>  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="5344c-117">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 提供下列用於監視複寫代理程式的對話方塊：</span><span class="sxs-lookup"><span data-stu-id="5344c-117">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] provides the following dialog boxes for monitoring replication agents:</span></span>  
  
-   <span data-ttu-id="5344c-118">**[檢視快照集代理程式的狀態]** (針對所有發行集)</span><span class="sxs-lookup"><span data-stu-id="5344c-118">**View Snapshot Agent Status** (for all publications)</span></span>  
  
-   <span data-ttu-id="5344c-119">**[檢視記錄讀取器代理程式的狀態]** (針對所有交易式發行集)</span><span class="sxs-lookup"><span data-stu-id="5344c-119">**View Log Reader Agent Status** (for all transactional publications)</span></span>  
  
-   <span data-ttu-id="5344c-120">**[檢視同步處理的狀態]** (針對所有訂閱；此對話方塊允許存取「散發代理程式」與「合併代理程式」)</span><span class="sxs-lookup"><span data-stu-id="5344c-120">**View Synchronization Status** (for all subscriptions; this dialog box allows access to the Distribution Agent and the Merge Agent)</span></span>  
  
 <span data-ttu-id="5344c-121">「複寫監視器」提供每個代理程式的其他資訊，並提供對「佇列讀取器代理程式」的監視(如果使用的話)。</span><span class="sxs-lookup"><span data-stu-id="5344c-121">Replication Monitor provides additional information about each agent and provides monitoring for the Queue Reader Agent, if it is used.</span></span> <span data-ttu-id="5344c-122">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="5344c-122">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
#### <a name="to-monitor-the-snapshot-agent-and-log-reader-agent"></a><span data-ttu-id="5344c-123">若要監視快照集代理程式和記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="5344c-123">To monitor the Snapshot Agent and Log Reader Agent</span></span>  
  
1.  <span data-ttu-id="5344c-124">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="5344c-124">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="5344c-125">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5344c-125">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="5344c-126">以滑鼠右鍵按一下發行集，然後按一下 **[檢視記錄讀取器代理程式的狀態]** 或 **[檢視快照集代理程式的狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="5344c-126">Right-click a publication, and then click **View Log Reader Agent Status** or **View Snapshot Agent Status**.</span></span>  
  
4.  <span data-ttu-id="5344c-127">在 **[檢視記錄讀取器代理程式的狀態]** 或 **[檢視快照集代理程式的狀態]** 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="5344c-127">In the **View Log Reader Agent Status** or **View Snapshot Agent Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="5344c-128">檢視代理程式狀態。</span><span class="sxs-lookup"><span data-stu-id="5344c-128">View agent status.</span></span>  
  
    -   <span data-ttu-id="5344c-129">如有必要，啟動或停止代理程式。</span><span class="sxs-lookup"><span data-stu-id="5344c-129">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="5344c-130">按一下 **[監視器]** 以啟動 **[複寫監視器]** 。</span><span class="sxs-lookup"><span data-stu-id="5344c-130">Click **Monitor** to launch **Replication Monitor**.</span></span>  
  
5.  <span data-ttu-id="5344c-131">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="5344c-131">Click **Close**.</span></span>  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-publisher"></a><span data-ttu-id="5344c-132">若要監視散發代理程式與合併代理程式 (從發行者)</span><span class="sxs-lookup"><span data-stu-id="5344c-132">To monitor the Distribution Agent and Merge Agent (from the Publisher)</span></span>  
  
1.  <span data-ttu-id="5344c-133">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="5344c-133">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="5344c-134">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5344c-134">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="5344c-135">展開要監視之訂閱的發行集。</span><span class="sxs-lookup"><span data-stu-id="5344c-135">Expand the publication for the subscription you want to monitor.</span></span>  
  
4.  <span data-ttu-id="5344c-136">以滑鼠右鍵按一下訂閱，然後按一下 **[檢視同步處理的狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="5344c-136">Right-click the subscription, and then click **View Synchronization Status**.</span></span>  
  
5.  <span data-ttu-id="5344c-137">在 **[檢視同步處理的狀態]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="5344c-137">In the **View Synchronization Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="5344c-138">檢視代理程式狀態。</span><span class="sxs-lookup"><span data-stu-id="5344c-138">View agent status.</span></span>  
  
    -   <span data-ttu-id="5344c-139">如有必要，啟動或停止代理程式。</span><span class="sxs-lookup"><span data-stu-id="5344c-139">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="5344c-140">對於發送訂閱，按一下 **[監視器]** 以啟動 **[複寫監視器]** 。</span><span class="sxs-lookup"><span data-stu-id="5344c-140">For push subscriptions, click **Monitor** to launch **Replication Monitor**.</span></span>  
  
    -   <span data-ttu-id="5344c-141">對於提取訂閱，按一下 **[檢視作業記錄]** 以啟動 **[記錄檔檢視器]** ，該檢視器會顯示代理程式記錄的輸出。</span><span class="sxs-lookup"><span data-stu-id="5344c-141">For pull subscriptions, click **View Job History** to launch the **Log File Viewer**, which displays output from the agent log.</span></span>  
  
6.  <span data-ttu-id="5344c-142">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="5344c-142">Click **Close**.</span></span>  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-subscriber"></a><span data-ttu-id="5344c-143">若要監視散發代理程式與合併代理程式 (從訂閱者)</span><span class="sxs-lookup"><span data-stu-id="5344c-143">To monitor the Distribution Agent and Merge Agent (from the Subscriber)</span></span>  
  
1.  <span data-ttu-id="5344c-144">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="5344c-144">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="5344c-145">展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5344c-145">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="5344c-146">以滑鼠右鍵按一下您要監視的訂閱，然後按一下 **[檢視同步處理的狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="5344c-146">Right-click the subscription you want to monitor, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="5344c-147">在 **[檢視同步處理的狀態]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="5344c-147">In the **View Synchronization Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="5344c-148">檢視代理程式狀態。</span><span class="sxs-lookup"><span data-stu-id="5344c-148">View agent status.</span></span>  
  
    -   <span data-ttu-id="5344c-149">如有必要，啟動或停止代理程式。</span><span class="sxs-lookup"><span data-stu-id="5344c-149">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="5344c-150">按一下 **[檢視作業記錄]** 以啟動 **[記錄檔檢視器]** ，該檢視器會顯示代理程式記錄的輸出。</span><span class="sxs-lookup"><span data-stu-id="5344c-150">Click **View Job History** to launch the **Log File Viewer**, which displays output from the agent log.</span></span>  
  
5.  <span data-ttu-id="5344c-151">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="5344c-151">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5344c-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5344c-152">See Also</span></span>  
 <span data-ttu-id="5344c-153">[監視複寫](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="5344c-153">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 [<span data-ttu-id="5344c-154">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="5344c-154">Replication Agents Overview</span></span>](../agents/replication-agents-overview.md)  
  
  
