---
title: 使用複寫監視器監視效能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Log Reader Agent, monitoring
- Replication Monitor, performance
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication]
ms.assetid: f212397d-1bfd-496b-a246-668952891d09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d02cb17aae5dfe72a9660de62e516e61313ef03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593938"
---
# <a name="monitor-performance-with-replication-monitor"></a><span data-ttu-id="c3f13-102">使用複寫監視器監視效能</span><span class="sxs-lookup"><span data-stu-id="c3f13-102">Monitor Performance with Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="c3f13-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫監視器可讓您使用下列方法來監視異動複寫與合併式複寫的效能：</span><span class="sxs-lookup"><span data-stu-id="c3f13-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor allows you to monitor the performance of transactional replication and merge replication in the following ways:</span></span>  
  
-   <span data-ttu-id="c3f13-104">設定警告和臨界值</span><span class="sxs-lookup"><span data-stu-id="c3f13-104">Setting warnings and thresholds</span></span>  
  
-   <span data-ttu-id="c3f13-105">檢視效能度量</span><span class="sxs-lookup"><span data-stu-id="c3f13-105">Viewing performance measurements</span></span>  
  
-   <span data-ttu-id="c3f13-106">以追蹤 Token 決定延遲 (異動複寫)</span><span class="sxs-lookup"><span data-stu-id="c3f13-106">Determining latency with tracer tokens (transactional replication)</span></span>  
  
-   <span data-ttu-id="c3f13-107">檢視詳細的同步處理統計資料 (合併式複寫)</span><span class="sxs-lookup"><span data-stu-id="c3f13-107">Viewing detailed synchronization statistics (merge replication)</span></span>  
  
-   <span data-ttu-id="c3f13-108">檢視交易和傳遞時間 (異動複寫)</span><span class="sxs-lookup"><span data-stu-id="c3f13-108">Viewing transactions and delivery time (transactional replication)</span></span>  
  
## <a name="set-warnings-and-thresholds"></a><span data-ttu-id="c3f13-109">設定警告和臨界值</span><span class="sxs-lookup"><span data-stu-id="c3f13-109">Set Warnings and Thresholds</span></span>  
 <span data-ttu-id="c3f13-110">「複寫監視器」允許您啟用一些效能條件的警告。</span><span class="sxs-lookup"><span data-stu-id="c3f13-110">Replication Monitor allows you to enable warnings for a number of performance conditions.</span></span> <span data-ttu-id="c3f13-111">在您啟用警告時，必須指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-111">When you enable a warning, you specify a threshold.</span></span> <span data-ttu-id="c3f13-112">當達到或超過該臨界值時，會在訂閱和與之同步的發行集之 **[狀態]** 資料行中顯示警告 (除非需要顯示優先權更高的問題)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-112">When that threshold is met or exceeded, a warning is displayed in the **Status** column for the subscription and the publication with which it synchronizes (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="c3f13-113">除了在複寫監視器顯示警告外，達到臨界值也會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="c3f13-113">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="c3f13-114">您可以啟用下列效能條件的警告：</span><span class="sxs-lookup"><span data-stu-id="c3f13-114">You can enable warnings for the following performance conditions:</span></span>  
  
-   <span data-ttu-id="c3f13-115">超過指定的延遲 (交易受發行者認可與對應交易受訂閱者認可之間所經過的時間)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-115">Exceeding the specified latency (the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber).</span></span>  
  
     <span data-ttu-id="c3f13-116">這可以套用於異動複寫。</span><span class="sxs-lookup"><span data-stu-id="c3f13-116">This applies to transactional replication.</span></span> <span data-ttu-id="c3f13-117">若已達到或超過指定臨界值，狀態顯示為 **[效能嚴重不足]** 。</span><span class="sxs-lookup"><span data-stu-id="c3f13-117">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span>  
  
-   <span data-ttu-id="c3f13-118">超過指定的同步處理時間。</span><span class="sxs-lookup"><span data-stu-id="c3f13-118">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="c3f13-119">這可以套用於合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="c3f13-119">This applies to merge replication.</span></span> <span data-ttu-id="c3f13-120">若已達到或超過指定臨界值，狀態顯示為 **[長期執行合併]** 。</span><span class="sxs-lookup"><span data-stu-id="c3f13-120">If the specified threshold is met or exceeded, the status is displayed as **Long-running merge**.</span></span> <span data-ttu-id="c3f13-121">您可以為撥號連接和區域網路 (LAN) 連接指定不同的臨界值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-121">You can specify different thresholds for dial-up and Local Area Network (LAN) connections.</span></span>  
  
-   <span data-ttu-id="c3f13-122">在給定時間內處理的資料列數達不到指定數目。</span><span class="sxs-lookup"><span data-stu-id="c3f13-122">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="c3f13-123">這可以套用於合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="c3f13-123">This applies to merge replication.</span></span> <span data-ttu-id="c3f13-124">若已達到或超過指定臨界值，狀態顯示為 **[效能嚴重不足]** 。</span><span class="sxs-lookup"><span data-stu-id="c3f13-124">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span> <span data-ttu-id="c3f13-125">您可以為撥號連接和 LAN 連接指定不同的臨界值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-125">You can specify different thresholds for dial-up and LAN connections.</span></span>  
  
 <span data-ttu-id="c3f13-126">如需相關資訊，請參閱 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-126">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
## <a name="view-performance-measurements"></a><span data-ttu-id="c3f13-127">檢視效能度量</span><span class="sxs-lookup"><span data-stu-id="c3f13-127">View Performance Measurements</span></span>  
 <span data-ttu-id="c3f13-128">複寫監視器在發行集的 **[目前的平均效能]** 和 **[目前最差效能]** 資料行，以及訂閱的 **[效能]** 資料行，顯示異動複寫與合併式複寫的效能品質的值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-128">Replication Monitor displays performance quality values for transactional replication and merge replication in the **Current Average Performance** and **Current Worst Performance** columns for publications and the **Performance** column for subscriptions.</span></span> <span data-ttu-id="c3f13-129">值如下：</span><span class="sxs-lookup"><span data-stu-id="c3f13-129">The values are:</span></span>  
  
-   <span data-ttu-id="c3f13-130">非常好</span><span class="sxs-lookup"><span data-stu-id="c3f13-130">Excellent</span></span>  
  
-   <span data-ttu-id="c3f13-131">好</span><span class="sxs-lookup"><span data-stu-id="c3f13-131">Good</span></span>  
  
-   <span data-ttu-id="c3f13-132">普通</span><span class="sxs-lookup"><span data-stu-id="c3f13-132">Fair</span></span>  
  
-   <span data-ttu-id="c3f13-133">差</span><span class="sxs-lookup"><span data-stu-id="c3f13-133">Poor</span></span>  
  
-   <span data-ttu-id="c3f13-134">嚴重不足 (僅限於異動複寫)</span><span class="sxs-lookup"><span data-stu-id="c3f13-134">Critical (transactional replication only)</span></span>  
  
 <span data-ttu-id="c3f13-135">使用下列方法判斷這些值：</span><span class="sxs-lookup"><span data-stu-id="c3f13-135">The values are determined in the following ways:</span></span>  
  
-   <span data-ttu-id="c3f13-136">對於異動複寫，效能品質由延遲臨界值決定。</span><span class="sxs-lookup"><span data-stu-id="c3f13-136">For transactional replication, performance quality is determined by the latency threshold.</span></span> <span data-ttu-id="c3f13-137">如果不設定臨界值，則不顯示值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-137">If the threshold is not set, a value is not displayed.</span></span> <span data-ttu-id="c3f13-138">下表顯示了臨界值和效能品質值之間的交互關聯。</span><span class="sxs-lookup"><span data-stu-id="c3f13-138">The following table shows the correlation between the threshold and the performance quality value.</span></span> <span data-ttu-id="c3f13-139">例如，如果將臨界值設定為 60 秒，而實際延遲為 30 秒，則延遲為臨界值的 50%，結果值為「好」。</span><span class="sxs-lookup"><span data-stu-id="c3f13-139">For example, if the threshold is set to 60 seconds and the actual latency is 30 seconds, latency is 50% of the threshold, resulting in a value of Good.</span></span>  
  
    |<span data-ttu-id="c3f13-140">非常好</span><span class="sxs-lookup"><span data-stu-id="c3f13-140">Excellent</span></span>|<span data-ttu-id="c3f13-141">好</span><span class="sxs-lookup"><span data-stu-id="c3f13-141">Good</span></span>|<span data-ttu-id="c3f13-142">普通</span><span class="sxs-lookup"><span data-stu-id="c3f13-142">Fair</span></span>|<span data-ttu-id="c3f13-143">差</span><span class="sxs-lookup"><span data-stu-id="c3f13-143">Poor</span></span>|<span data-ttu-id="c3f13-144">重大</span><span class="sxs-lookup"><span data-stu-id="c3f13-144">Critical</span></span>|  
    |---------------|----------|----------|----------|--------------|  
    |<span data-ttu-id="c3f13-145">0 - 34%</span><span class="sxs-lookup"><span data-stu-id="c3f13-145">0 - 34%</span></span>|<span data-ttu-id="c3f13-146">35 - 59%</span><span class="sxs-lookup"><span data-stu-id="c3f13-146">35 - 59%</span></span>|<span data-ttu-id="c3f13-147">60 - 84%</span><span class="sxs-lookup"><span data-stu-id="c3f13-147">60 - 84%</span></span>|<span data-ttu-id="c3f13-148">85 - 99%</span><span class="sxs-lookup"><span data-stu-id="c3f13-148">85 - 99%</span></span>|<span data-ttu-id="c3f13-149">100% +</span><span class="sxs-lookup"><span data-stu-id="c3f13-149">100% +</span></span>|  
  
-   <span data-ttu-id="c3f13-150">對於合併式複寫，效能品質與臨界值無關 (如果在 **[狀態]** 資料行中顯示的值為 **[效能嚴重不足]** ，則資料列處理臨界值將不作判斷)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-150">For merge replication, performance quality is independent of either threshold (the row processing threshold does determine if a value of **Performance critical** is displayed in the **Status** column).</span></span> <span data-ttu-id="c3f13-151">透過將個別訂閱效能與具有相同連接類型 (撥號或 LAN) 之發行集訂閱的平均記錄效能進行比較，對效能品質進行判斷。</span><span class="sxs-lookup"><span data-stu-id="c3f13-151">Performance quality is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="c3f13-152">在相同連接類型上發生過五次同步處理，且每次同步處理都具有 50 或更多個變更之後，複寫監視器才會顯示值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-152">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="c3f13-153">如果發生 50 個 (含) 以上變更的同步處理不及五個，或者最近一次同步處理少於 50 個變更，則「複寫監視器」不會顯示值。</span><span class="sxs-lookup"><span data-stu-id="c3f13-153">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, Replication Monitor does not display a value.</span></span>  
  
     <span data-ttu-id="c3f13-154">下表顯示了平均效能和效能品質值之間的交互關聯。</span><span class="sxs-lookup"><span data-stu-id="c3f13-154">The following table shows the correlation between the average performance and the performance quality value.</span></span> <span data-ttu-id="c3f13-155">例如，如果十個「訂閱者」透過 LAN 連接以每秒平均 100 個資料列的速率進行同步處理，而其中一個訂閱則是以每秒 125 個資料列的速率進行同步處理，這個「訂閱者」的同步處理效能平均為 125%，結果值為「好」。</span><span class="sxs-lookup"><span data-stu-id="c3f13-155">For example, if ten Subscribers have synchronized over a LAN connection with an average rate of 100 rows per second, and one of the subscriptions then synchronizes at a rate of 125 rows per second, the performance for that Subscriber's synchronization is 125% of the average, resulting in a value of Good.</span></span>  
  
    |<span data-ttu-id="c3f13-156">非常好</span><span class="sxs-lookup"><span data-stu-id="c3f13-156">Excellent</span></span>|<span data-ttu-id="c3f13-157">好</span><span class="sxs-lookup"><span data-stu-id="c3f13-157">Good</span></span>|<span data-ttu-id="c3f13-158">普通</span><span class="sxs-lookup"><span data-stu-id="c3f13-158">Fair</span></span>|<span data-ttu-id="c3f13-159">差</span><span class="sxs-lookup"><span data-stu-id="c3f13-159">Poor</span></span>|  
    |---------------|----------|----------|----------|  
    |<span data-ttu-id="c3f13-160">151+%</span><span class="sxs-lookup"><span data-stu-id="c3f13-160">151+%</span></span>|<span data-ttu-id="c3f13-161">76 - 150%</span><span class="sxs-lookup"><span data-stu-id="c3f13-161">76 - 150%</span></span>|<span data-ttu-id="c3f13-162">26 - 75%</span><span class="sxs-lookup"><span data-stu-id="c3f13-162">26 - 75%</span></span>|<span data-ttu-id="c3f13-163">0 - 25%</span><span class="sxs-lookup"><span data-stu-id="c3f13-163">0 - 25%</span></span>|  
  
 <span data-ttu-id="c3f13-164">如需有關檢視訂閱資訊的詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-164">For more information about viewing subscription information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="determine-latency-with-tracer-tokens"></a><span data-ttu-id="c3f13-165">使用追蹤 Token 判斷延遲</span><span class="sxs-lookup"><span data-stu-id="c3f13-165">Determine Latency with Tracer Tokens</span></span>  
 <span data-ttu-id="c3f13-166">異動複寫可允許您藉由在發行集資料庫的交易記錄中插入 Token (少量資料)，並記錄到達散發者和訂閱者所需花費的時間，以測量系統中的延遲。</span><span class="sxs-lookup"><span data-stu-id="c3f13-166">Transactional replication allows you to measure the latency in a system by inserting a token (a small amount of data) in the transaction log of the publication database and recording how long it takes to arrive at the Distributor and Subscribers.</span></span> <span data-ttu-id="c3f13-167">Token 亦可讓您識別資料是否未到達散發者或訂閱者。</span><span class="sxs-lookup"><span data-stu-id="c3f13-167">The token also allows you to identify if data is not reaching the Distributor or Subscriber.</span></span> <span data-ttu-id="c3f13-168">如需相關資訊，請參閱 [針對異動複寫測量延遲及驗證連接](measure-latency-and-validate-connections-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-168">For more information, see [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
## <a name="view-detailed-synchronization-performance-for-merge-replication"></a><span data-ttu-id="c3f13-169">檢視合併式複寫的詳細同步處理效能</span><span class="sxs-lookup"><span data-stu-id="c3f13-169">View Detailed Synchronization Performance for Merge Replication</span></span>  
 <span data-ttu-id="c3f13-170">針對合併式複寫，複寫監視器於同步處理時顯示每個已處理發行項的詳細資訊，包括每個處理階段花費的時間 (上傳變更、下載變更等等)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-170">For merge replication, Replication Monitor displays detailed statistics for each article processed during synchronization, including the amount of time spent in each processing phase (uploading changes, downloading changes, and so on).</span></span> <span data-ttu-id="c3f13-171">這樣有助於找出導致過慢的特定資料表，同時也是解決合併訂閱效能問題的最佳地點。</span><span class="sxs-lookup"><span data-stu-id="c3f13-171">It can help pinpoint specific tables that are causing slow downs and is the best place to troubleshoot performance issues with merge subscriptions.</span></span> <span data-ttu-id="c3f13-172">如需有關檢視詳細統計資料的詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-172">For more information on viewing detailed statistics, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="view-transactions-and-delivery-time-for-transactional-replication"></a><span data-ttu-id="c3f13-173">檢視異動複寫的交易和傳遞時間</span><span class="sxs-lookup"><span data-stu-id="c3f13-173">View Transactions and Delivery Time for Transactional Replication</span></span>  
 <span data-ttu-id="c3f13-174">對於異動複寫，「複寫監視器」會顯示有關下列內容的資訊：尚未散發到「訂閱者」之散發資料庫中的交易數，以及散發這些交易的預估時間。</span><span class="sxs-lookup"><span data-stu-id="c3f13-174">For transactional replication, Replication Monitor displays information about the number of transactions in the distribution database that have not yet been distributed to a Subscriber and the estimated time for distributing these transactions.</span></span> <span data-ttu-id="c3f13-175">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="c3f13-175">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f13-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3f13-176">See Also</span></span>  
 <span data-ttu-id="c3f13-177">[監視複寫](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="c3f13-177">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 [<span data-ttu-id="c3f13-178">Set Thresholds and Warnings in Replication Monitor</span><span class="sxs-lookup"><span data-stu-id="c3f13-178">Set Thresholds and Warnings in Replication Monitor</span></span>](set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
