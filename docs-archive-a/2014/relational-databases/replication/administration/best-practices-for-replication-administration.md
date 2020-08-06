---
title: 複寫管理的最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- administering replication, best practices
- replication [SQL Server], administering
ms.assetid: 850e8a87-b34c-4934-afb5-a1104f118ba8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 16652561fa873c5d8a33d8826372837744543e70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705078"
---
# <a name="best-practices-for-replication-administration"></a><span data-ttu-id="51ef7-102">複寫管理的最佳做法</span><span class="sxs-lookup"><span data-stu-id="51ef7-102">Best Practices for Replication Administration</span></span>
  <span data-ttu-id="51ef7-103">設定複寫之後，請務必了解如何管理複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="51ef7-103">After you have configured replication, it is important to understand how to administer a replication topology.</span></span> <span data-ttu-id="51ef7-104">這個主題提供各個範疇的基本最佳做法指導，並可透過連結方式分別取得進一步資訊。</span><span class="sxs-lookup"><span data-stu-id="51ef7-104">This topic provides basic best practice guidance in a number of areas with links to more information for each area.</span></span> <span data-ttu-id="51ef7-105">除了依照本主題中提出的最佳做法指導以外，請考慮閱讀常見問答集主題來熟悉常見的問題：[複寫管理員的常見問題集](frequently-asked-questions-for-replication-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-105">In addition to following the best practice guidance presented in this topic, consider reading through the frequently asked questions topic to acquaint yourself with common questions and issues: [Frequently Asked Questions for Replication Administrators](frequently-asked-questions-for-replication-administrators.md).</span></span>  
  
 <span data-ttu-id="51ef7-106">將最佳做法指南分成兩個方面非常有用：</span><span class="sxs-lookup"><span data-stu-id="51ef7-106">It is useful to divide the best practice guidance into two areas:</span></span>  
  
-   <span data-ttu-id="51ef7-107">下列資訊涵蓋應為所有複寫拓撲實作的最佳做法：</span><span class="sxs-lookup"><span data-stu-id="51ef7-107">The following information covers best practices that should be implemented for all replication topologies:</span></span>  
  
    -   <span data-ttu-id="51ef7-108">開發並測試備份與還原策略。</span><span class="sxs-lookup"><span data-stu-id="51ef7-108">Develop and test a backup and restore strategy.</span></span>  
  
    -   <span data-ttu-id="51ef7-109">編寫複寫拓撲指令碼。</span><span class="sxs-lookup"><span data-stu-id="51ef7-109">Script the replication topology.</span></span>  
  
    -   <span data-ttu-id="51ef7-110">建立臨界值和警示。</span><span class="sxs-lookup"><span data-stu-id="51ef7-110">Create thresholds and alerts.</span></span>  
  
    -   <span data-ttu-id="51ef7-111">監視複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="51ef7-111">Monitor the replication topology.</span></span>  
  
    -   <span data-ttu-id="51ef7-112">必要時，建立效能基準線並微調複寫。</span><span class="sxs-lookup"><span data-stu-id="51ef7-112">Establish performance baselines and tune replication if necessary.</span></span>  
  
-   <span data-ttu-id="51ef7-113">下列資訊涵蓋對於您的拓撲來說應予以考慮，但可能不是必要的最佳做法：</span><span class="sxs-lookup"><span data-stu-id="51ef7-113">The following information covers best practices that should be considered, but might not be required for your topology:</span></span>  
  
    -   <span data-ttu-id="51ef7-114">定期驗證資料。</span><span class="sxs-lookup"><span data-stu-id="51ef7-114">Validate data periodically.</span></span>  
  
    -   <span data-ttu-id="51ef7-115">透過設定檔調整代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="51ef7-115">Adjust agent parameters through profiles.</span></span>  
  
    -   <span data-ttu-id="51ef7-116">調整發行集和散發保留期限。</span><span class="sxs-lookup"><span data-stu-id="51ef7-116">Adjust publication and distribution retention periods.</span></span>  
  
    -   <span data-ttu-id="51ef7-117">了解應用程式需求變更時如何變更發行項與發行集屬性。</span><span class="sxs-lookup"><span data-stu-id="51ef7-117">Understand how to change article and publication properties if application requirements change.</span></span>  
  
    -   <span data-ttu-id="51ef7-118">了解應用程式需求變更時如何變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="51ef7-118">Understand how to make schema changes if application requirements change.</span></span>  
  
## <a name="develop-and-test-a-backup-and-restore-strategy"></a><span data-ttu-id="51ef7-119">開發並測試備份與還原策略</span><span class="sxs-lookup"><span data-stu-id="51ef7-119">Develop and test a backup and restore strategy</span></span>  
 <span data-ttu-id="51ef7-120">所有的資料庫應定期備份，並應定期測試還原這些備份的功能；複寫的資料庫也不能例外。</span><span class="sxs-lookup"><span data-stu-id="51ef7-120">All databases should be backed up on a regular basis, and the ability to restore those backups should be tested periodically; replicated databases are no different.</span></span> <span data-ttu-id="51ef7-121">下列資料庫應定期備份：</span><span class="sxs-lookup"><span data-stu-id="51ef7-121">The following databases should be backed up regularly:</span></span>  
  
-   <span data-ttu-id="51ef7-122">發行集資料庫</span><span class="sxs-lookup"><span data-stu-id="51ef7-122">Publication database</span></span>  
  
-   <span data-ttu-id="51ef7-123">散發資料庫</span><span class="sxs-lookup"><span data-stu-id="51ef7-123">Distribution database</span></span>  
  
-   <span data-ttu-id="51ef7-124">訂閱資料庫</span><span class="sxs-lookup"><span data-stu-id="51ef7-124">Subscription databases</span></span>  
  
-   <span data-ttu-id="51ef7-125">「發行者」、「散發者」及所有「訂閱者」端的**msdb** 資料庫和 **master** 資料庫</span><span class="sxs-lookup"><span data-stu-id="51ef7-125">**msdb** database and **master** database at the Publisher, Distributor, and all Subscribers</span></span>  
  
 <span data-ttu-id="51ef7-126">針對複寫的資料庫進行資料的備份與還原時，需要特別地注意。</span><span class="sxs-lookup"><span data-stu-id="51ef7-126">Replicated databases require special attention with regards to backing up and restoring data.</span></span> <span data-ttu-id="51ef7-127">如需詳細資訊，請參閱 [備份及還原複寫的資料庫](back-up-and-restore-replicated-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-127">For more information, see [Back Up and Restore Replicated Databases](back-up-and-restore-replicated-databases.md).</span></span>  
  
## <a name="script-the-replication-topology"></a><span data-ttu-id="51ef7-128">編寫複寫拓撲指令碼</span><span class="sxs-lookup"><span data-stu-id="51ef7-128">Script the replication topology</span></span>  
 <span data-ttu-id="51ef7-129">拓撲中的所有複寫元件都應作為損毀復原計畫的一部份來編寫指令碼，而指令碼也可以用於自動執行重複性工作。</span><span class="sxs-lookup"><span data-stu-id="51ef7-129">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="51ef7-130">指令碼包含實作已編寫指令碼之複寫元件所必要的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 系統預存程序，如發行集或訂閱。</span><span class="sxs-lookup"><span data-stu-id="51ef7-130">A script contains the [!INCLUDE[tsql](../../../includes/tsql-md.md)] system stored procedures necessary to implement the replication component(s) scripted, such as a publication or subscription.</span></span> <span data-ttu-id="51ef7-131">指令碼可以在精靈中建立 (例如 [新增發行集精靈])，或可在建立元件之後，於 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中建立。</span><span class="sxs-lookup"><span data-stu-id="51ef7-131">Scripts can be created in a wizard (such as the New Publication Wizard) or in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] after you create a component.</span></span> <span data-ttu-id="51ef7-132">您可使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或 **sqlcmd**，檢視、修改和執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="51ef7-132">You can view, modify, and run the script using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or **sqlcmd**.</span></span> <span data-ttu-id="51ef7-133">指令碼可以和備份檔案一起儲存，萬一必須重新設定複寫拓撲時即可使用。</span><span class="sxs-lookup"><span data-stu-id="51ef7-133">Scripts can be stored with backup files to be used in case a replication topology must be reconfigured.</span></span> <span data-ttu-id="51ef7-134">如需詳細資訊，請參閱 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-134">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
 <span data-ttu-id="51ef7-135">如果任何屬性被變更，則應對該元件重新編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="51ef7-135">A component should be rescripted if any property changes are made.</span></span> <span data-ttu-id="51ef7-136">若您在異動複寫中使用自訂預存程序，每個程序副本會與指令碼同時儲存；若程序變更，則副本必須更新 (程序通常在結構描述變更或改變應用程式需求時進行更新)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-136">If you use custom stored procedures with transactional replication, a copy of each procedure should be stored with the scripts; the copy should be updated if the procedure changes (procedures are typically updated due to schema changes or changing application requirements).</span></span> <span data-ttu-id="51ef7-137">如需自訂程序的詳細資訊，請參閱[指定交易式發行項變更的傳播方式](../transactional/transactional-articles-specify-how-changes-are-propagated.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-137">For more information about custom procedures, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
## <a name="establish-performance-baselines-and-tune-replication-if-necessary"></a><span data-ttu-id="51ef7-138">必要時，建立效能基準線並微調複寫</span><span class="sxs-lookup"><span data-stu-id="51ef7-138">Establish performance baselines and tune replication if necessary</span></span>  
 <span data-ttu-id="51ef7-139">在設定複寫前，建議您先熟悉影響複寫效能的因素：</span><span class="sxs-lookup"><span data-stu-id="51ef7-139">Before replication is configured, it is recommended to familiarize yourself with the factors that affect replication performance:</span></span>  
  
-   <span data-ttu-id="51ef7-140">伺服器和網路硬體</span><span class="sxs-lookup"><span data-stu-id="51ef7-140">Server and network hardware</span></span>  
  
-   <span data-ttu-id="51ef7-141">資料庫設計</span><span class="sxs-lookup"><span data-stu-id="51ef7-141">Database design</span></span>  
  
-   <span data-ttu-id="51ef7-142">散發者組態</span><span class="sxs-lookup"><span data-stu-id="51ef7-142">Distributor configuration</span></span>  
  
-   <span data-ttu-id="51ef7-143">發行集設計與選項</span><span class="sxs-lookup"><span data-stu-id="51ef7-143">Publication design and options</span></span>  
  
-   <span data-ttu-id="51ef7-144">篩選設計與使用</span><span class="sxs-lookup"><span data-stu-id="51ef7-144">Filter design and use</span></span>  
  
-   <span data-ttu-id="51ef7-145">訂閱選項</span><span class="sxs-lookup"><span data-stu-id="51ef7-145">Subscription options</span></span>  
  
-   <span data-ttu-id="51ef7-146">快照集選項</span><span class="sxs-lookup"><span data-stu-id="51ef7-146">Snapshot options</span></span>  
  
-   <span data-ttu-id="51ef7-147">代理程式參數</span><span class="sxs-lookup"><span data-stu-id="51ef7-147">Agent parameters</span></span>  
  
-   <span data-ttu-id="51ef7-148">維護</span><span class="sxs-lookup"><span data-stu-id="51ef7-148">Maintenance</span></span>  
  
 <span data-ttu-id="51ef7-149">在設定複寫後，建議您開發一個效能基準線，它可讓您判斷複寫在您的應用程式及拓撲之一般工作負載下的行為。</span><span class="sxs-lookup"><span data-stu-id="51ef7-149">After replication is configured, it is recommended to develop a performance baseline, which will allow you to determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="51ef7-150">使用複寫監視器和系統監視器來判斷下列五個複寫效能維度的特定數值：</span><span class="sxs-lookup"><span data-stu-id="51ef7-150">Use Replication Monitor and System Monitor to determine typical numbers for the following five dimensions of replication performance:</span></span>  
  
-   <span data-ttu-id="51ef7-151">延遲：資料變更要在複寫拓撲的節點之間傳播所需要花費的時間。</span><span class="sxs-lookup"><span data-stu-id="51ef7-151">Latency: the amount of time it takes for a data change to be propagated between nodes in a replication topology.</span></span>  
  
-   <span data-ttu-id="51ef7-152">輸送量：系統在一段長時間可承受的複寫活動量 (以某段時間傳遞的命令數量來測量)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-152">Throughput: the amount of replication activity (measured in commands delivered over a period of time) a system can sustain over time.</span></span>  
  
-   <span data-ttu-id="51ef7-153">並行：在系統上可同步操作的複寫處理數量。</span><span class="sxs-lookup"><span data-stu-id="51ef7-153">Concurrency: the number of replication processes that can operate on a system simultaneously.</span></span>  
  
-   <span data-ttu-id="51ef7-154">同步處理的持續時間：完成給定同步處理所需要的時間長度。</span><span class="sxs-lookup"><span data-stu-id="51ef7-154">Duration of synchronization: how long it takes a given synchronization to complete.</span></span>  
  
-   <span data-ttu-id="51ef7-155">資源消耗：用來作為複寫處理結果的硬體和網路資源。</span><span class="sxs-lookup"><span data-stu-id="51ef7-155">Resource consumption: hardware and network resources used as a result of replication processing.</span></span>  
  
 <span data-ttu-id="51ef7-156">延遲和輸送量與異動複寫關係密切，因為在異動複寫上建立的系統通常需要低度延遲和高輸送量。</span><span class="sxs-lookup"><span data-stu-id="51ef7-156">Latency and throughput are most relevant to transactional replication, because systems built on transactional replication generally require low latency and high throughput.</span></span> <span data-ttu-id="51ef7-157">並行和同步處理的持續時間與合併式複寫關係密切，因為在合併式複寫上建立的系統通常有大量的訂閱者，同時發行者可與這些訂閱者擁有許多並行的同步處理。</span><span class="sxs-lookup"><span data-stu-id="51ef7-157">Concurrency and duration of synchronization are most relevant to merge replication, because systems built on merge replication often have a large number of Subscribers, and a Publisher can have a significant number of concurrent synchronizations with these Subscribers.</span></span>  
  
 <span data-ttu-id="51ef7-158">建立比較基準數之後，設定複寫監視器的臨界值。</span><span class="sxs-lookup"><span data-stu-id="51ef7-158">After you have established baseline numbers, set thresholds in Replication Monitor.</span></span> <span data-ttu-id="51ef7-159">如需詳細資訊，請參閱[在複寫監視器中設定臨界值和警告](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)和[使用複寫代理程式事件的警示](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-159">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span> <span data-ttu-id="51ef7-160">若您遭遇效能上的問題，建議閱讀上述改善效能主題中所有建議事項，並針對您遇到的問題，套用可能產生影響的變更。</span><span class="sxs-lookup"><span data-stu-id="51ef7-160">If you encounter a performance problem, it is recommended to read through the suggestions in the enhancing performance topics listed above and to apply changes in areas that affect the issues you are encountering.</span></span>  
  
## <a name="create-thresholds-and-alerts"></a><span data-ttu-id="51ef7-161">建立臨界值和警示</span><span class="sxs-lookup"><span data-stu-id="51ef7-161">Create thresholds and alerts</span></span>  
 <span data-ttu-id="51ef7-162">「複寫監視器」允許您設定大量與狀態及效能相關的臨界值。</span><span class="sxs-lookup"><span data-stu-id="51ef7-162">Replication Monitor allows you to set a number of thresholds related to status and performance.</span></span> <span data-ttu-id="51ef7-163">建議為您的拓撲設定適當的臨界值；當達到臨界值時，會顯示警告，並可以選擇性地將警示傳送到電子郵件帳戶、呼叫器或其他裝置。</span><span class="sxs-lookup"><span data-stu-id="51ef7-163">It is recommended to set the appropriate thresholds for your topology; if a threshold is reached, a warning is displayed, and, optionally, an alert can be sent to an e-mail account, a pager, or other device.</span></span> <span data-ttu-id="51ef7-164">如需相關資訊，請參閱 [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-164">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="51ef7-165">除了與監視臨界值相關聯的警示之外，複寫還提供大量用於回應複寫代理程式動作之預先定義的警示。</span><span class="sxs-lookup"><span data-stu-id="51ef7-165">In addition to the alerts that can be associated with monitoring thresholds, replication provides a number of predefined alerts that respond to replication agent actions.</span></span> <span data-ttu-id="51ef7-166">管理員可以使用這些警示隨時獲悉複寫拓撲的狀態。</span><span class="sxs-lookup"><span data-stu-id="51ef7-166">These alerts can be used by an administrator to stay informed about the state of the replication topology.</span></span> <span data-ttu-id="51ef7-167">建議閱讀描述該警示的主題，並使用適合您管理需要的任何警示 (必要時，也可以建立其他警示)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-167">It is recommended to read through the topic describing the alerts and to use any that fit your administration needs (it is also possible to create additional alerts if necessary).</span></span> <span data-ttu-id="51ef7-168">如需詳細資訊，請參閱[使用複寫代理程式事件的警示](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-168">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
## <a name="monitor-the-replication-topology"></a><span data-ttu-id="51ef7-169">監視複寫拓撲</span><span class="sxs-lookup"><span data-stu-id="51ef7-169">Monitor the replication topology</span></span>  
 <span data-ttu-id="51ef7-170">在設定複寫拓撲且已設定臨界值及警示後，建議您定期監視複寫。</span><span class="sxs-lookup"><span data-stu-id="51ef7-170">After the replication topology is in place and thresholds and alerts have been configured, it is recommended to regularly monitor replication.</span></span> <span data-ttu-id="51ef7-171">監控複寫拓撲是部署複寫時很重要的層面。</span><span class="sxs-lookup"><span data-stu-id="51ef7-171">Monitoring a replication topology is an important aspect of deploying replication.</span></span> <span data-ttu-id="51ef7-172">由於已散發複寫活動，因此必須跨越所有複寫相關的電腦，追蹤活動和狀態</span><span class="sxs-lookup"><span data-stu-id="51ef7-172">Because replication activity is distributed, it is essential to track activity and status across all computers involved in replication.</span></span> <span data-ttu-id="51ef7-173">下列工具可用來監視複寫：</span><span class="sxs-lookup"><span data-stu-id="51ef7-173">The following tools can be used to monitor replication:</span></span>  
  
-   <span data-ttu-id="51ef7-174">「複寫監視器」是監視複寫的最重要的工具，可讓您監視複寫拓撲的全面健全狀況。</span><span class="sxs-lookup"><span data-stu-id="51ef7-174">Replication Monitor is the most important tool for monitoring replication, allowing you to monitor the overall health of a replication topology.</span></span> <span data-ttu-id="51ef7-175">如需詳細資訊，請參閱 [Monitoring Replication](../monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-175">For more information, see [Monitoring Replication](../monitoring-replication.md).</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="51ef7-176">和 Replication Management Objects (RMO) 提供監視複寫的介面。</span><span class="sxs-lookup"><span data-stu-id="51ef7-176">and Replication Management Objects (RMO) provide interfaces for monitoring replication.</span></span> <span data-ttu-id="51ef7-177">如需詳細資訊，請參閱 [Monitoring Replication](../monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-177">For more information, see [Monitoring Replication](../monitoring-replication.md).</span></span>  
  
-   <span data-ttu-id="51ef7-178">「系統監視器」也可用於監視複寫效能。</span><span class="sxs-lookup"><span data-stu-id="51ef7-178">System Monitor can also be useful for monitoring replication performance.</span></span> <span data-ttu-id="51ef7-179">如需相關資訊，請參閱 [Monitoring Replication with System Monitor](../monitor/monitoring-replication-with-system-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-179">For more information, see [Monitoring Replication with System Monitor](../monitor/monitoring-replication-with-system-monitor.md).</span></span>  
  
## <a name="validate-data-periodically"></a><span data-ttu-id="51ef7-180">定期驗證資料</span><span class="sxs-lookup"><span data-stu-id="51ef7-180">Validate data periodically</span></span>  
 <span data-ttu-id="51ef7-181">複寫並不需要進行驗證，但建議對異動複寫和合併式複寫定期執行驗證。</span><span class="sxs-lookup"><span data-stu-id="51ef7-181">Validation is not required by replication, but it is recommended to run validation periodically for transactional replication and merge replication.</span></span> <span data-ttu-id="51ef7-182">驗證允許您驗證「訂閱者」端的資料與「發行者」端的資料是否相符合。</span><span class="sxs-lookup"><span data-stu-id="51ef7-182">Validation allows you to verify that data at the Subscriber matches data at the Publisher.</span></span> <span data-ttu-id="51ef7-183">成功的驗證則表示，在那個時間點，「發行者」端的所有變更都已複寫到「訂閱者」端 (同時，如果「訂閱者」端支援更新，則「訂閱者」端的所有變更也都會複寫到「發行者」端)，而且這兩個資料庫將保持同步。</span><span class="sxs-lookup"><span data-stu-id="51ef7-183">Successful validation indicates that at that point in time all changes from the Publisher have been replicated to the Subscriber (and from the Subscriber to the Publisher if updates are supported at the Subscriber) and that the two databases are in sync.</span></span>  
  
 <span data-ttu-id="51ef7-184">建議根據發行集資料庫的備份排程執行驗證。</span><span class="sxs-lookup"><span data-stu-id="51ef7-184">It is recommended that validation be performed according to the backup schedule of the publication database.</span></span> <span data-ttu-id="51ef7-185">例如，如果發行集資料庫每週進行一次完整備份，則驗證會在備份完成後每週執行一次。</span><span class="sxs-lookup"><span data-stu-id="51ef7-185">For example, if the publication database has a full backup once per week, validation could be run once per week after the backup completes.</span></span> <span data-ttu-id="51ef7-186">如需詳細資訊，請參閱[驗證複寫的資料](../validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-186">For more information, see [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="use-agent-profiles-to-change-agent-parameters-if-necessary"></a><span data-ttu-id="51ef7-187">必要時，使用代理程式設定檔變更代理程式參數</span><span class="sxs-lookup"><span data-stu-id="51ef7-187">Use agent profiles to change agent parameters if necessary</span></span>  
 <span data-ttu-id="51ef7-188">代理程式設定檔提供一個設定複寫代理程式參數的便利方法。</span><span class="sxs-lookup"><span data-stu-id="51ef7-188">Agent profiles provide a convenient method of setting replication agent parameters.</span></span> <span data-ttu-id="51ef7-189">參數也可以在代理程式命令列指定，但是如果您需要變更參數值，則一般更適合使用預先定義的代理程式設定檔或者建立一個新設定檔。</span><span class="sxs-lookup"><span data-stu-id="51ef7-189">Parameters can also be specified on the agent command line, but it is typically more appropriate to use a predefined agent profile or to create a new profile if you need to change the value of a parameter.</span></span> <span data-ttu-id="51ef7-190">例如，如果您使用合併式複寫，同時「訂閱者」從寬頻連接移到撥號連接，請考慮為「合併代理程式」使用 **慢速連結** 設定檔；此設定檔會使用一組更適合慢速通訊連結的參數。</span><span class="sxs-lookup"><span data-stu-id="51ef7-190">For example, if you are using merge replication and a Subscriber moves from a broadband connection to a dialup connection, consider using the **slow link** profile for the Merge Agent; this profile uses a set of parameters that are better suited to the slower communications link.</span></span> <span data-ttu-id="51ef7-191">如需相關資訊，請參閱 [Replication Agent Profiles](../agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-191">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="adjust-publication-and-distribution-retention-periods-if-necessary"></a><span data-ttu-id="51ef7-192">必要時，調整發行集和散發保留期限</span><span class="sxs-lookup"><span data-stu-id="51ef7-192">Adjust publication and distribution retention periods if necessary</span></span>  
 <span data-ttu-id="51ef7-193">異動複寫和合併式複寫使用保留期限，對交易在散發資料庫中儲存的時間及訂閱必須進行同步處理的頻率分別進行判斷。</span><span class="sxs-lookup"><span data-stu-id="51ef7-193">Transactional replication and merge replication use retention periods to determine, respectively, how long transactions are stored in the distribution database, and how frequently a subscription must synchronize.</span></span> <span data-ttu-id="51ef7-194">建議在開始階段使用預設設定，但要監視您的拓撲以判斷設定是否需要調整。</span><span class="sxs-lookup"><span data-stu-id="51ef7-194">It is recommended to use the default settings initially, but to monitor your topology to determine if the settings require adjustment.</span></span> <span data-ttu-id="51ef7-195">例如，在合併式複寫的情況下，發行集保留期限 (預設為 14 天) 會決定中繼資料在系統資料表中的儲存時間。</span><span class="sxs-lookup"><span data-stu-id="51ef7-195">For example, in the case of merge replication, the publication retention period (which defaults to 14 days) determines how long metadata is stored in system tables.</span></span> <span data-ttu-id="51ef7-196">如果訂閱總是在五天內同步，則考慮將設定調整為一個較低的數字，這樣可以減少中繼資料，並可能提供更好的效能。</span><span class="sxs-lookup"><span data-stu-id="51ef7-196">If subscriptions always synchronize within five days, consider adjusting the setting to a lower number, which will reduce metadata and possibly provide better performance.</span></span> <span data-ttu-id="51ef7-197">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-197">For more information, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="understand-how-to-modify-publications-if-application-requirements-change"></a><span data-ttu-id="51ef7-198">了解應用程式需求變更時如何修改發行集</span><span class="sxs-lookup"><span data-stu-id="51ef7-198">Understand how to modify publications if application requirements change</span></span>  
 <span data-ttu-id="51ef7-199">建立發行集之後，可能需要加入或卸除發行項，或者變更發行集與發行項屬性。</span><span class="sxs-lookup"><span data-stu-id="51ef7-199">After you have created a publication, it might be necessary to add or drop articles, or change publication and article properties.</span></span> <span data-ttu-id="51ef7-200">建立發行集之後即允許多數變更。但在某些情況下，必須產生新的發行集快照集和 (或) 重新初始化訂閱到發行集。</span><span class="sxs-lookup"><span data-stu-id="51ef7-200">Most changes are allowed after a publication is created, but in some cases, it is necessary to generate a new snapshot for a publication and/or reinitialize subscriptions to the publication.</span></span> <span data-ttu-id="51ef7-201">如需詳細資訊，請參閱[變更發行集與發行項屬性](../publish/change-publication-and-article-properties.md)和[在現有發行集中新增和卸除發行項](../publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-201">For more information, see [Change Publication and Article Properties](../publish/change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](../publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
## <a name="understand-how-to-make-schema-changes-if-application-requirements-change"></a><span data-ttu-id="51ef7-202">了解應用程式需求變更時如何變更結構描述</span><span class="sxs-lookup"><span data-stu-id="51ef7-202">Understand how to make schema changes if application requirements change</span></span>  
 <span data-ttu-id="51ef7-203">許多情況下，在應用程式運行後需要進行結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="51ef7-203">In many cases, schema changes are required after an application is in production.</span></span> <span data-ttu-id="51ef7-204">在複寫拓撲中，這些變更必須經常傳播給所有的「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="51ef7-204">In a replication topology, these changes must often be propagated to all Subscribers.</span></span> <span data-ttu-id="51ef7-205">複寫支援對已發行物件進行大範圍的結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="51ef7-205">Replication supports a wide range of schema changes to published objects.</span></span> <span data-ttu-id="51ef7-206">當您對「[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行者」端適當的已發行物件進行下列任何結構描述變更時，依預設，該變更會傳播給所有的「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」：</span><span class="sxs-lookup"><span data-stu-id="51ef7-206">When you make any of the following schema changes on the appropriate published object at a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, that change is propagated by default to all [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="51ef7-207">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="51ef7-207">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="51ef7-208">ALTER VIEW</span><span class="sxs-lookup"><span data-stu-id="51ef7-208">ALTER VIEW</span></span>  
  
-   <span data-ttu-id="51ef7-209">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="51ef7-209">ALTER PROCEDURE</span></span>  
  
-   <span data-ttu-id="51ef7-210">ALTER FUNCTION</span><span class="sxs-lookup"><span data-stu-id="51ef7-210">ALTER FUNCTION</span></span>  
  
-   <span data-ttu-id="51ef7-211">ALTER TRIGGER</span><span class="sxs-lookup"><span data-stu-id="51ef7-211">ALTER TRIGGER</span></span>  
  
 <span data-ttu-id="51ef7-212">如需詳細資訊，請參閱[對發行集資料庫進行結構描述變更](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef7-212">For more information, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ef7-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51ef7-213">See Also</span></span>  
 [<span data-ttu-id="51ef7-214">複寫管理常見問題集</span><span class="sxs-lookup"><span data-stu-id="51ef7-214">Replication Administration FAQ</span></span>](frequently-asked-questions-for-replication-administrators.md)  
  
  
