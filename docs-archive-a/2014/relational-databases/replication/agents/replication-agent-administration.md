---
title: 複寫代理程式管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, administering
- Log Reader Agent, administering
- Queue Reader Agent, administering
- shared agents [SQL Server replication]
- Merge Agent, administering
- Distribution Agent, administering
- agents [SQL Server replication], administering
- replication cleanup jobs [SQL Server]
- administering replication, agents
- replication [SQL Server], administering
- independent agents [SQL Server replication]
ms.assetid: f27186b8-b1b2-4da0-8b2b-91f632c2ab7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 99cf9be6b31310e5ae0ebac3c096851ac4f63452
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593961"
---
# <a name="replication-agent-administration"></a><span data-ttu-id="ef2c1-102">複寫代理程式管理</span><span class="sxs-lookup"><span data-stu-id="ef2c1-102">Replication Agent Administration</span></span>
  <span data-ttu-id="ef2c1-103">複寫代理程式可執行許多有關複寫的工作，包含建立結構描述和資料的副本、偵測「發行者」或「訂閱者」端的更新，以及在伺服器之間傳播變更。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-103">Replication agents carry out many of the tasks associated with replication, including creating copies of schema and data, detecting updates at the Publisher or Subscriber, and propagating changes between servers.</span></span> <span data-ttu-id="ef2c1-104">根據預設，複寫代理程式在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 作業步驟下執行。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-104">By default, replication agents run under [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="ef2c1-105">此代理程式只不過是可執行檔，所以也可以從命令列和批次指令碼直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-105">The agents are simply executables, so they can also be called directly from the command line and from batch scripts.</span></span> <span data-ttu-id="ef2c1-106">每個複寫代理程式都支援一組用於控制其執行方式的執行時期參數；這些參數在代理程式設定檔或命令列中指定。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-106">Each replication agent supports a set of run-time parameters used to control how it runs; these parameters are specified in an agent profile or on the command line.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ef2c1-107">依預設，安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時會停用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服務，除非明確選擇在安裝期間自動啟動該服務。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-107">By default, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service is disabled when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is installed unless you explicitly choose to autostart the service during installation.</span></span>  
  
 <span data-ttu-id="ef2c1-108">複寫代理程式檔案位於 [!INCLUDE[ssInstallPathVar](../../../includes/ssinstallpathvar-md.md)]\COM 之下。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-108">Replication agent files are located under [!INCLUDE[ssInstallPathVar](../../../includes/ssinstallpathvar-md.md)]\COM.</span></span> <span data-ttu-id="ef2c1-109">下表列出了複寫的可執行檔名稱和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-109">The following table lists the replication executable names and file names.</span></span> <span data-ttu-id="ef2c1-110">按一下代理程式的連結以檢視其參數參考。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-110">Click the link for an agent to view its parameter reference.</span></span>  
  
|<span data-ttu-id="ef2c1-111">代理程式可執行檔</span><span class="sxs-lookup"><span data-stu-id="ef2c1-111">Agent Executable</span></span>|<span data-ttu-id="ef2c1-112">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="ef2c1-112">File Name</span></span>|  
|----------------------|---------------|  
|[<span data-ttu-id="ef2c1-113">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="ef2c1-113">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|<span data-ttu-id="ef2c1-114">snapshot.exe</span><span class="sxs-lookup"><span data-stu-id="ef2c1-114">snapshot.exe</span></span>|  
|[<span data-ttu-id="ef2c1-115">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="ef2c1-115">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|<span data-ttu-id="ef2c1-116">distrib.exe</span><span class="sxs-lookup"><span data-stu-id="ef2c1-116">distrib.exe</span></span>|  
|[<span data-ttu-id="ef2c1-117">複寫記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-117">Replication Log Reader Agent</span></span>](replication-log-reader-agent.md)|<span data-ttu-id="ef2c1-118">logread.exe</span><span class="sxs-lookup"><span data-stu-id="ef2c1-118">logread.exe</span></span>|  
|[<span data-ttu-id="ef2c1-119">複寫佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-119">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)|<span data-ttu-id="ef2c1-120">qrdrsvc.exe</span><span class="sxs-lookup"><span data-stu-id="ef2c1-120">qrdrsvc.exe</span></span>|  
|[<span data-ttu-id="ef2c1-121">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="ef2c1-121">Replication Merge Agent</span></span>](replication-merge-agent.md)|<span data-ttu-id="ef2c1-122">replmerg.exe</span><span class="sxs-lookup"><span data-stu-id="ef2c1-122">replmerg.exe</span></span>|  
  
 <span data-ttu-id="ef2c1-123">除了複寫代理程式外，複寫還有許多依排程和依要求來執行維護的作業。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-123">In addition to replication agents, replication has a number of jobs that perform scheduled and on-demand maintenance.</span></span>  
  
 <span data-ttu-id="ef2c1-124">**若要執行代理程式和維護作業**</span><span class="sxs-lookup"><span data-stu-id="ef2c1-124">**To run agents and maintenance jobs**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="ef2c1-125">和複寫監視器：[啟動和停止複寫代理程式 &#40;SQL Server Management Studio&#41;](start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-125">and Replication Monitor: [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="ef2c1-126">複寫程式設計：[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)</span><span class="sxs-lookup"><span data-stu-id="ef2c1-126">Replication programming: [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)</span></span>  
  
## <a name="agent-profiles"></a><span data-ttu-id="ef2c1-127">代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="ef2c1-127">Agent Profiles</span></span>  
 <span data-ttu-id="ef2c1-128">設定複寫時，會在散發者上安裝一組代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-128">When replication is configured, a set of agent profiles is installed on the Distributor.</span></span> <span data-ttu-id="ef2c1-129">代理程式設定檔包含一組參數，代理程式每次執行時都會使用這組參數：每個代理程式在啟動過程中都會登入散發者，並查詢其設定檔內的參數。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-129">An agent profile contains a set of parameters that are used each time an agent runs: each agent logs in to the Distributor during its startup process and queries for the parameters in its profile.</span></span> <span data-ttu-id="ef2c1-130">複寫為每個代理程式提供預設的設定檔，並為記錄讀取代理程式、散發代理程式及合併代理程式提供其他預先定義的設定檔。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-130">Replication provides a default profile for each agent and additional predefined profiles for the Log Reader Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="ef2c1-131">除了提供的設定檔之外，您也可以建立適合自己的應用程式需求的設定檔。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-131">In addition to the profiles provided, you can create profiles suited to your application requirements.</span></span> <span data-ttu-id="ef2c1-132">如需相關資訊，請參閱 [Replication Agent Profiles](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-132">For more information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="ef2c1-133">如需直接指定命令列參數的資訊，請參閱[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-133">For information about specifying command line parameters directly, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="monitoring-replication-agents"></a><span data-ttu-id="ef2c1-134">監視複寫代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-134">Monitoring Replication Agents</span></span>  
 <span data-ttu-id="ef2c1-135">「複寫監視器」允許您檢視資訊並執行與每個複寫代理程式相關聯的工作。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-135">Replication Monitor allows you to view information and perform tasks associated with each replication agent.</span></span> <span data-ttu-id="ef2c1-136">下列清單包含每個代理程式、可以在複寫監視器上找到的索引標籤，以及到說明如何存取這些索引標籤之主題的連結：</span><span class="sxs-lookup"><span data-stu-id="ef2c1-136">The following list includes each agent, the tabs in the Replication Monitor on which it can be found, and a link to a topic that explains how to access these tabs:</span></span>  
  
-   <span data-ttu-id="ef2c1-137">下列代理程式與複寫監視器中的發行集相關聯：</span><span class="sxs-lookup"><span data-stu-id="ef2c1-137">The following agents are associated with publications in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="ef2c1-138">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-138">Snapshot Agent</span></span>  
  
    -   <span data-ttu-id="ef2c1-139">記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-139">Log Reader Agent</span></span>  
  
    -   <span data-ttu-id="ef2c1-140">佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-140">Queue Reader Agent</span></span>  
  
     <span data-ttu-id="ef2c1-141">透過 [**代理**程式] 索引標籤，存取與這些代理程式相關聯的資訊和工作。如需詳細資訊，請參閱[使用複寫監視器來查看資訊及執行](../monitor/view-information-and-perform-tasks-replication-monitor.md)工作。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-141">Access information and tasks associated with these agents through the **Agents** tab. For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="ef2c1-142">下列代理程式與複寫監視器中的訂閱相關聯：</span><span class="sxs-lookup"><span data-stu-id="ef2c1-142">The following agents are associated with subscriptions in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="ef2c1-143">散發代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-143">Distribution Agent</span></span>  
  
    -   <span data-ttu-id="ef2c1-144">合併代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-144">Merge Agent</span></span>  
  
     <span data-ttu-id="ef2c1-145">透過下列索引標籤，可存取與這些代理程式建立關聯的資訊和工作：[訂閱監看清單] (適用於每個「發行者」) 或 [所有訂閱] 索引標籤 (適用於每個發行集)。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-145">Access information and tasks associated with these agents through the following tabs: **Subscription Watch List** (available for each Publisher) or the **All Subscriptions** tab (available for each publication).</span></span> <span data-ttu-id="ef2c1-146">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](../monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-146">For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="independent-and-shared-agents"></a><span data-ttu-id="ef2c1-147">獨立與共用的代理程式</span><span class="sxs-lookup"><span data-stu-id="ef2c1-147">Independent and Shared Agents</span></span>  
 <span data-ttu-id="ef2c1-148">獨立代理程式即服務一個訂閱的代理程式。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-148">An independent agent is an agent that services one subscription.</span></span> <span data-ttu-id="ef2c1-149">共用的代理程式會服務多個訂閱；如果使用相同共用代理程式的多個訂閱需要同步，依預設，它們會在佇列中等候，該共用代理程式會一次服務其中之一。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-149">A shared agent services multiple subscriptions; if multiple subscriptions using the same shared agent need to synchronize, by default they wait in a queue, and the shared agent services them one at a time.</span></span> <span data-ttu-id="ef2c1-150">使用獨立代理程式會降低延遲，因為代理程式會在訂閱需要同步時就緒。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-150">Latency is reduced when using independent agents because the agent is ready whenever the subscription needs to be synchronized.</span></span> <span data-ttu-id="ef2c1-151">合併式複寫通常使用獨立代理程式，依預設，異動複寫會使用在「新增發行集精靈」中建立的發行集之獨立代理程式 (在舊版 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，依預設，異動複寫則使用共用代理程式)。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-151">Merge replication always uses independent agents, and transactional replication uses independent agents by default for publications created in the New Publication Wizard (in previous versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], transactional replication used shared agents by default).</span></span>  
  
## <a name="replication-maintenance-jobs"></a><span data-ttu-id="ef2c1-152">複寫維護作業</span><span class="sxs-lookup"><span data-stu-id="ef2c1-152">Replication Maintenance Jobs</span></span>  
 <span data-ttu-id="ef2c1-153">複寫使用下列作業執行依排程和視需要的維護。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-153">Replication uses the following jobs to perform scheduled and on-demand maintenance.</span></span>  
  
|<span data-ttu-id="ef2c1-154">清除作業</span><span class="sxs-lookup"><span data-stu-id="ef2c1-154">Clean up job</span></span>|<span data-ttu-id="ef2c1-155">描述</span><span class="sxs-lookup"><span data-stu-id="ef2c1-155">Description</span></span>|<span data-ttu-id="ef2c1-156">預設排程</span><span class="sxs-lookup"><span data-stu-id="ef2c1-156">Default schedule</span></span>|  
|------------------|-----------------|----------------------|  
|<span data-ttu-id="ef2c1-157">清除代理程式記錄：散發</span><span class="sxs-lookup"><span data-stu-id="ef2c1-157">Agent History Clean Up: Distribution</span></span>|<span data-ttu-id="ef2c1-158">從散發資料庫移除複寫代理程式的記錄。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-158">Removes replication agent history from the distribution database.</span></span>|<span data-ttu-id="ef2c1-159">每 10 分鐘執行</span><span class="sxs-lookup"><span data-stu-id="ef2c1-159">Runs every ten minutes</span></span>|  
|<span data-ttu-id="ef2c1-160">清除散發：散發</span><span class="sxs-lookup"><span data-stu-id="ef2c1-160">Distribution Clean Up: Distribution</span></span>|<span data-ttu-id="ef2c1-161">從散發資料庫移除複寫的交易。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-161">Removes replicated transactions from the distribution database.</span></span> <span data-ttu-id="ef2c1-162">停用在最長散發保留期限內未同步的訂閱。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-162">Deactivates subscriptions that have not been synchronized within the maximum distribution retention period.</span></span>|<span data-ttu-id="ef2c1-163">每 10 分鐘執行</span><span class="sxs-lookup"><span data-stu-id="ef2c1-163">Runs every ten minutes</span></span>|  
|<span data-ttu-id="ef2c1-164">到期的訂閱清除</span><span class="sxs-lookup"><span data-stu-id="ef2c1-164">Expired Subscription Clean Up</span></span>|<span data-ttu-id="ef2c1-165">偵測並移除散發資料庫中到期的訂閱。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-165">Detects and removes expired subscriptions from publication databases.</span></span>|<span data-ttu-id="ef2c1-166">每天早上 1:00 執行</span><span class="sxs-lookup"><span data-stu-id="ef2c1-166">Runs every day at 1:00 A.M.</span></span>|  
|<span data-ttu-id="ef2c1-167">重新初始化資料驗證失敗的訂閱</span><span class="sxs-lookup"><span data-stu-id="ef2c1-167">Reinitialize Subscriptions Having Data Validation Failures</span></span>|<span data-ttu-id="ef2c1-168">偵測使資料驗證失敗的所有訂閱，並將其標示為重新初始化。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-168">Detects all subscriptions that have data validation failures and marks them for reinitialization.</span></span> <span data-ttu-id="ef2c1-169">下次「合併代理程式」或「散發代理程式」執行時，將在「訂閱者」端套用新的快照集。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-169">The next time the Merge Agent or Distribution Agent runs, a new snapshot will be applied at the Subscribers.</span></span>|<span data-ttu-id="ef2c1-170">沒有預設排程 (依預設值未啟動)</span><span class="sxs-lookup"><span data-stu-id="ef2c1-170">No default schedule (not enabled by default).</span></span>|  
|<span data-ttu-id="ef2c1-171">複寫代理程式檢查</span><span class="sxs-lookup"><span data-stu-id="ef2c1-171">Replication Agents Checkup</span></span>|<span data-ttu-id="ef2c1-172">偵測並未動態記錄歷程的複寫代理程式。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-172">Detects replication agents that are not actively logging history.</span></span> <span data-ttu-id="ef2c1-173">如果作業步驟失敗，則其會寫入 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-173">It writes to the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows event log if a job step fails.</span></span>|<span data-ttu-id="ef2c1-174">每十分鐘執行一次。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-174">Runs every ten minutes.</span></span>|  
|<span data-ttu-id="ef2c1-175">散發的複寫監視重新整理器</span><span class="sxs-lookup"><span data-stu-id="ef2c1-175">Replication monitoring refresher for distribution</span></span>|<span data-ttu-id="ef2c1-176">重新整理「複寫監視器」使用的快取查詢。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-176">Refreshes cached queries used by Replication Monitor..</span></span>|<span data-ttu-id="ef2c1-177">連續執行。</span><span class="sxs-lookup"><span data-stu-id="ef2c1-177">Runs continuously.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef2c1-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef2c1-178">See Also</span></span>  
 [<span data-ttu-id="ef2c1-179">監視複寫</span><span class="sxs-lookup"><span data-stu-id="ef2c1-179">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
