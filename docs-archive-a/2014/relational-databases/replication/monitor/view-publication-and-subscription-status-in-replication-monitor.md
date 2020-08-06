---
title: 在複寫監視器中檢視發行集和訂閱狀態 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, monitoring
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- publications [SQL Server replication], viewing information
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication], publication status
- monitoring performance [SQL Server replication], subscription status
- subscriptions [SQL Server replication], viewing status
- Replication Monitor, publication and subscription status
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f1f714e18a961546a4e5a7f6709beca8d525800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709173"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a><span data-ttu-id="3400c-102">在複寫監視器中檢視發行集和訂閱狀態</span><span class="sxs-lookup"><span data-stu-id="3400c-102">View Publication and Subscription Status in Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="3400c-103">「複寫監視器」會顯示發行集 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 和訂閱的狀態資訊：</span><span class="sxs-lookup"><span data-stu-id="3400c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor displays status information for publications and subscriptions:</span></span>  
  
-   <span data-ttu-id="3400c-104">發行集的狀態是由其訂閱的最高優先權狀態所決定。</span><span class="sxs-lookup"><span data-stu-id="3400c-104">The status of a publication is determined by the highest priority status of its subscriptions.</span></span> <span data-ttu-id="3400c-105">例如，如果發行集的某個訂閱發生錯誤，而另一個訂閱發生效能問題，則會針對該發行集顯示錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="3400c-105">For example, if one subscription to a publication has an error and another has a performance issue, a status of error is displayed for the publication.</span></span>  
  
-   <span data-ttu-id="3400c-106">訂閱的狀態是由服務訂閱的代理程式狀態所決定。</span><span class="sxs-lookup"><span data-stu-id="3400c-106">The status of a subscription is determined by the status of the agents that service the subscription.</span></span> <span data-ttu-id="3400c-107">對於合併複寫來說，這是指「合併代理程式」。</span><span class="sxs-lookup"><span data-stu-id="3400c-107">For merge replication, this is the Merge Agent.</span></span> <span data-ttu-id="3400c-108">對於異動複寫來說，這是指「記錄讀取器代理程式」或「散發代理程式」(會顯示較高優先權的狀態；而如果使用佇列更新訂閱，狀態亦可由「佇列讀取器代理程式」決定)。</span><span class="sxs-lookup"><span data-stu-id="3400c-108">For transactional replication, this is either the Log Reader Agent or the Distribution Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span> <span data-ttu-id="3400c-109">對於快照集複寫來說，這是指「快照集代理程式」或「散發代理程式」(會顯示較高優先權的狀態)。</span><span class="sxs-lookup"><span data-stu-id="3400c-109">For snapshot replication, this is the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="3400c-110">下列各節中的資料表會列出發行集和訂閱的可能狀態值。</span><span class="sxs-lookup"><span data-stu-id="3400c-110">Tables in the following sections list the possible status values for publications and subscriptions.</span></span> <span data-ttu-id="3400c-111">這三種狀態值只會在達到或超過臨界值時顯示：</span><span class="sxs-lookup"><span data-stu-id="3400c-111">Three of the status values are displayed only if a threshold is met or exceeded:</span></span>  
  
-   <span data-ttu-id="3400c-112">訂閱過期</span><span class="sxs-lookup"><span data-stu-id="3400c-112">Expiring subscription</span></span>  
  
     <span data-ttu-id="3400c-113">這個狀態值適用所有複寫類型。</span><span class="sxs-lookup"><span data-stu-id="3400c-113">This status value applies to all types of replication.</span></span> <span data-ttu-id="3400c-114">如需相關資訊，請參閱 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3400c-114">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="3400c-115">效能嚴重不足</span><span class="sxs-lookup"><span data-stu-id="3400c-115">Performance critical</span></span>  
  
     <span data-ttu-id="3400c-116">這個狀態值適用異動複寫和合併複寫。</span><span class="sxs-lookup"><span data-stu-id="3400c-116">This status value applies to transactional replication and merge replication.</span></span> <span data-ttu-id="3400c-117">如需詳細資訊，請參閱[使用複寫監視器監視效能](monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3400c-117">For more information, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="3400c-118">長期執行合併</span><span class="sxs-lookup"><span data-stu-id="3400c-118">Long-running merge</span></span>  
  
     <span data-ttu-id="3400c-119">這個狀態值適用合併複寫。</span><span class="sxs-lookup"><span data-stu-id="3400c-119">This status value applies to merge replication.</span></span> <span data-ttu-id="3400c-120">如需詳細資訊，請參閱[使用複寫監視器監視效能](monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3400c-120">For more information, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="3400c-121">除了發行集和訂閱狀態之外，合併複寫還提供發行項層級的統計資料，其中提供的詳細資訊包括：合併階段需花多長的時間完成、已花費多少時間處理指定的發行項、「訂閱者」使用的連接類型，以及其他重要資訊。</span><span class="sxs-lookup"><span data-stu-id="3400c-121">In addition to publication and subscription status, merge replication provides article-level statistics, which give detailed information about: how much longer a merge phase will take to complete; how much time was spent processing a given article; the type of connection a Subscriber is using; and other important information.</span></span> <span data-ttu-id="3400c-122">統計資料會在「複寫監視器」的「合併代理程式」視窗中顯示。</span><span class="sxs-lookup"><span data-stu-id="3400c-122">The statistics are displayed in the Merge Agent window in Replication Monitor.</span></span> <span data-ttu-id="3400c-123">快照集和異動複寫會提供有關「散發代理程式」處理的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="3400c-123">Snapshot and transactional replication provide detailed information on Distribution Agent processing.</span></span>  
  
 <span data-ttu-id="3400c-124">**檢視發行集和訂閱狀態**</span><span class="sxs-lookup"><span data-stu-id="3400c-124">**To view publication and subscription status**</span></span>  
  
-   <span data-ttu-id="3400c-125">複寫監視器：[使用複寫監視器來查看資訊及執行](view-information-and-perform-tasks-replication-monitor.md)工作。</span><span class="sxs-lookup"><span data-stu-id="3400c-125">Replication Monitor: [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>
  
  
## <a name="publication-status-values"></a><span data-ttu-id="3400c-126">發行集狀態值</span><span class="sxs-lookup"><span data-stu-id="3400c-126">Publication Status Values</span></span>  
 <span data-ttu-id="3400c-127">下表按優先權順序顯示發行集狀態值及其對應的圖示。</span><span class="sxs-lookup"><span data-stu-id="3400c-127">The following table shows publication status values and their corresponding icons in priority order.</span></span>  
  
|<span data-ttu-id="3400c-128">狀態</span><span class="sxs-lookup"><span data-stu-id="3400c-128">Status</span></span>|<span data-ttu-id="3400c-129">圖示</span><span class="sxs-lookup"><span data-stu-id="3400c-129">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="3400c-130">錯誤</span><span class="sxs-lookup"><span data-stu-id="3400c-130">Error</span></span>|<span data-ttu-id="3400c-131">![UI 圖示：錯誤](../media/repl-icon-error.gif "UI 圖示：錯誤")</span><span class="sxs-lookup"><span data-stu-id="3400c-131">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="3400c-132">效能嚴重不足</span><span class="sxs-lookup"><span data-stu-id="3400c-132">Performance critical</span></span>|<span data-ttu-id="3400c-133">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-133">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-134">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="3400c-134">Retrying failed command</span></span>|<span data-ttu-id="3400c-135">![UI 圖示：複寫代理程式重試](../media/repl-icon-retry.gif "UI 圖示：複寫代理程式重試")</span><span class="sxs-lookup"><span data-stu-id="3400c-135">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="3400c-136">確定</span><span class="sxs-lookup"><span data-stu-id="3400c-136">OK</span></span>|<span data-ttu-id="3400c-137">無</span><span class="sxs-lookup"><span data-stu-id="3400c-137">none</span></span>|  
  
## <a name="subscription-status-values"></a><span data-ttu-id="3400c-138">訂閱狀態值</span><span class="sxs-lookup"><span data-stu-id="3400c-138">Subscription Status Values</span></span>  
 <span data-ttu-id="3400c-139">下列各資料表按優先權順序顯示訂閱狀態值及其對應的圖示。</span><span class="sxs-lookup"><span data-stu-id="3400c-139">The following tables show subscription status values and their corresponding icons in priority order.</span></span> <span data-ttu-id="3400c-140">訂閱可同時處於兩種狀態，例如 **「即將過期/已過期」** 和 **「正在重試失敗的命令」**；此時會顯示最高優先權的狀態。</span><span class="sxs-lookup"><span data-stu-id="3400c-140">It is possible for a subscription to be in two states at the same time, such as **Expiring soon/Expired** and **Retrying failed command**; the highest priority status is displayed.</span></span>  
  
 <span data-ttu-id="3400c-141">**「效能嚴重不足」**、 **「即將過期/已過期」** 和 **「未初始化」** 等狀態值都是警告。</span><span class="sxs-lookup"><span data-stu-id="3400c-141">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized** are warnings.</span></span> <span data-ttu-id="3400c-142">當顯示警告時，「複寫監視器」也會顯示是否有代理程式正在執行。</span><span class="sxs-lookup"><span data-stu-id="3400c-142">When a warning is displayed, Replication Monitor also displays whether an agent is running.</span></span> <span data-ttu-id="3400c-143">例如，狀態可能是 **[執行中，效能嚴重不足]**。</span><span class="sxs-lookup"><span data-stu-id="3400c-143">For example, the status could be **Running, Performance critical**.</span></span>  
  
### <a name="transactional-subscriptions"></a><span data-ttu-id="3400c-144">交易式訂閱</span><span class="sxs-lookup"><span data-stu-id="3400c-144">Transactional subscriptions</span></span>  
  
|<span data-ttu-id="3400c-145">狀態</span><span class="sxs-lookup"><span data-stu-id="3400c-145">Status</span></span>|<span data-ttu-id="3400c-146">圖示</span><span class="sxs-lookup"><span data-stu-id="3400c-146">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="3400c-147">錯誤</span><span class="sxs-lookup"><span data-stu-id="3400c-147">Error</span></span>|<span data-ttu-id="3400c-148">![UI 圖示：錯誤](../media/repl-icon-error.gif "UI 圖示：錯誤")</span><span class="sxs-lookup"><span data-stu-id="3400c-148">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="3400c-149">效能嚴重不足</span><span class="sxs-lookup"><span data-stu-id="3400c-149">Performance critical</span></span>|<span data-ttu-id="3400c-150">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-150">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-151">「即將過期/已過期」</span><span class="sxs-lookup"><span data-stu-id="3400c-151">Expiring soon/Expired</span></span>|<span data-ttu-id="3400c-152">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-152">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-153">未初始化的訂閱</span><span class="sxs-lookup"><span data-stu-id="3400c-153">Uninitialized subscription</span></span>|<span data-ttu-id="3400c-154">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-154">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-155">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="3400c-155">Retrying failed command</span></span>|<span data-ttu-id="3400c-156">![UI 圖示：複寫代理程式重試](../media/repl-icon-retry.gif "UI 圖示：複寫代理程式重試")</span><span class="sxs-lookup"><span data-stu-id="3400c-156">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="3400c-157">未執行</span><span class="sxs-lookup"><span data-stu-id="3400c-157">Not running</span></span>|<span data-ttu-id="3400c-158">![UI 圖示：複寫代理程式已停止](../media/repl-icon-stopped.gif "UI 圖示：複寫代理程式已停止")</span><span class="sxs-lookup"><span data-stu-id="3400c-158">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
|<span data-ttu-id="3400c-159">執行中</span><span class="sxs-lookup"><span data-stu-id="3400c-159">Running</span></span>|<span data-ttu-id="3400c-160">![UI 圖示：複寫代理程式執行中](../media/repl-icon-running.gif "UI 圖示：複寫代理程式執行中")</span><span class="sxs-lookup"><span data-stu-id="3400c-160">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
  
### <a name="merge-subscriptions"></a><span data-ttu-id="3400c-161">合併訂閱</span><span class="sxs-lookup"><span data-stu-id="3400c-161">Merge subscriptions</span></span>  
  
|<span data-ttu-id="3400c-162">狀態</span><span class="sxs-lookup"><span data-stu-id="3400c-162">Status</span></span>|<span data-ttu-id="3400c-163">圖示</span><span class="sxs-lookup"><span data-stu-id="3400c-163">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="3400c-164">錯誤</span><span class="sxs-lookup"><span data-stu-id="3400c-164">Error</span></span>|<span data-ttu-id="3400c-165">![UI 圖示：錯誤](../media/repl-icon-error.gif "UI 圖示：錯誤")</span><span class="sxs-lookup"><span data-stu-id="3400c-165">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="3400c-166">效能嚴重不足</span><span class="sxs-lookup"><span data-stu-id="3400c-166">Performance critical</span></span>|<span data-ttu-id="3400c-167">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-167">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-168">長期執行合併</span><span class="sxs-lookup"><span data-stu-id="3400c-168">Long-running merge</span></span>|<span data-ttu-id="3400c-169">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-169">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-170">「即將過期/已過期」</span><span class="sxs-lookup"><span data-stu-id="3400c-170">Expiring soon/Expired</span></span>|<span data-ttu-id="3400c-171">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-171">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-172">未初始化的訂閱</span><span class="sxs-lookup"><span data-stu-id="3400c-172">Uninitialized subscription</span></span>|<span data-ttu-id="3400c-173">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-173">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-174">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="3400c-174">Retrying failed command</span></span>|<span data-ttu-id="3400c-175">![UI 圖示：複寫代理程式重試](../media/repl-icon-retry.gif "UI 圖示：複寫代理程式重試")</span><span class="sxs-lookup"><span data-stu-id="3400c-175">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="3400c-176">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="3400c-176">Synchronizing</span></span>|<span data-ttu-id="3400c-177">![UI 圖示：複寫代理程式執行中](../media/repl-icon-running.gif "UI 圖示：複寫代理程式執行中")</span><span class="sxs-lookup"><span data-stu-id="3400c-177">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
|<span data-ttu-id="3400c-178">未進行同步處理</span><span class="sxs-lookup"><span data-stu-id="3400c-178">Not Synchronizing</span></span>|<span data-ttu-id="3400c-179">![UI 圖示：複寫代理程式已停止](../media/repl-icon-stopped.gif "UI 圖示：複寫代理程式已停止")</span><span class="sxs-lookup"><span data-stu-id="3400c-179">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
  
### <a name="snapshot-subscriptions"></a><span data-ttu-id="3400c-180">快照集訂閱</span><span class="sxs-lookup"><span data-stu-id="3400c-180">Snapshot subscriptions</span></span>  
  
|<span data-ttu-id="3400c-181">狀態</span><span class="sxs-lookup"><span data-stu-id="3400c-181">Status</span></span>|<span data-ttu-id="3400c-182">圖示</span><span class="sxs-lookup"><span data-stu-id="3400c-182">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="3400c-183">錯誤</span><span class="sxs-lookup"><span data-stu-id="3400c-183">Error</span></span>|<span data-ttu-id="3400c-184">![UI 圖示：錯誤](../media/repl-icon-error.gif "UI 圖示：錯誤")</span><span class="sxs-lookup"><span data-stu-id="3400c-184">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="3400c-185">「即將過期/已過期」</span><span class="sxs-lookup"><span data-stu-id="3400c-185">Expiring soon/Expired</span></span>|<span data-ttu-id="3400c-186">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-186">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-187">未初始化的訂閱</span><span class="sxs-lookup"><span data-stu-id="3400c-187">Uninitialized subscription</span></span>|<span data-ttu-id="3400c-188">![UI 圖示：警告](../media/repl-icon-warn.gif "UI 圖示：警告")</span><span class="sxs-lookup"><span data-stu-id="3400c-188">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="3400c-189">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="3400c-189">Retrying failed command</span></span>|<span data-ttu-id="3400c-190">![UI 圖示：複寫代理程式重試](../media/repl-icon-retry.gif "UI 圖示：複寫代理程式重試")</span><span class="sxs-lookup"><span data-stu-id="3400c-190">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="3400c-191">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="3400c-191">Synchronizing</span></span>|<span data-ttu-id="3400c-192">![UI 圖示：複寫代理程式執行中](../media/repl-icon-running.gif "UI 圖示：複寫代理程式執行中")</span><span class="sxs-lookup"><span data-stu-id="3400c-192">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
|<span data-ttu-id="3400c-193">未進行同步處理</span><span class="sxs-lookup"><span data-stu-id="3400c-193">Not Synchronizing</span></span>|<span data-ttu-id="3400c-194">![UI 圖示：複寫代理程式已停止](../media/repl-icon-stopped.gif "UI 圖示：複寫代理程式已停止")</span><span class="sxs-lookup"><span data-stu-id="3400c-194">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3400c-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3400c-195">See Also</span></span>  
 [<span data-ttu-id="3400c-196">監視複寫</span><span class="sxs-lookup"><span data-stu-id="3400c-196">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
