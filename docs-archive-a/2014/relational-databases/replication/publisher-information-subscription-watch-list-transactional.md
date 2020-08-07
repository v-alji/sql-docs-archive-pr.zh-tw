---
title: 發行者資訊、訂閱監看清單 (交易式發行集、SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.tran.f1
ms.assetid: 6bc64ddb-5c86-4681-a391-77fc1d3c4e6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bf6d151b75bca1dbfd2e5ad8f7601fb1002e84be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584386"
---
# <a name="publisher-information-subscription-watch-list-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="40ce8-102">發行者資訊，訂閱監看清單 (交易式發行集，SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="40ce8-102">Publisher Information, Subscription Watch List (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="40ce8-103">執行 SQL Server 2005 和更新版本的散發者可以使用 **[訂閱監看清單]** 索引標籤；它是要用來在選取之發行者端的所有可用發行集上，顯示訂閱的資訊。</span><span class="sxs-lookup"><span data-stu-id="40ce8-103">The **Subscription Watch List** tab is available for Distributors running SQL Server 2005 and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="40ce8-104">您可以篩選訂閱清單以查看錯誤、警告以及任何執行不良的訂閱。</span><span class="sxs-lookup"><span data-stu-id="40ce8-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="40ce8-105">此索引標籤為管理員提供監視發行者端所有複寫活動的單一位置：複寫監視器會根據選取的複寫類型和 **[顯示]** 下拉式清單方塊中選擇的選項，顯示需要注意的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="40ce8-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="40ce8-106">由於此索引標籤上顯示的項目會依據目前的狀態與效能，因此唯有在目前符合 **[顯示]** 清單方塊中之選項的訂閱，才會在這個頁面上顯示。</span><span class="sxs-lookup"><span data-stu-id="40ce8-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="40ce8-107">選項。</span><span class="sxs-lookup"><span data-stu-id="40ce8-107">Options</span></span>  
 <span data-ttu-id="40ce8-108">如需詳細資訊以及與訂閱相關的工作，請以滑鼠右鍵按一下該訂閱的資料列，然後按一下捷徑功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="40ce8-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="40ce8-109">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="40ce8-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="40ce8-110">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="40ce8-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="40ce8-111">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="40ce8-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="40ce8-112">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="40ce8-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="40ce8-113">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="40ce8-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="40ce8-114">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="40ce8-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="40ce8-115">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="40ce8-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="40ce8-116">**顯示交易式訂閱**</span><span class="sxs-lookup"><span data-stu-id="40ce8-116">**Show Transactional Subscriptions**</span></span>  
 <span data-ttu-id="40ce8-117">針對選取之發行者，選取要顯示的訂閱類型 (交易式、快照式或合併式)。</span><span class="sxs-lookup"><span data-stu-id="40ce8-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="40ce8-118">**顯示**</span><span class="sxs-lookup"><span data-stu-id="40ce8-118">**Show**</span></span>  
 <span data-ttu-id="40ce8-119">針對選取之訂閱類型，選取要顯示的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="40ce8-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="40ce8-120">例如，您可以選取只顯示有錯誤的訂閱。</span><span class="sxs-lookup"><span data-stu-id="40ce8-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="40ce8-121">**狀態**</span><span class="sxs-lookup"><span data-stu-id="40ce8-121">**Status**</span></span>  
 <span data-ttu-id="40ce8-122">每個訂閱的狀態，這是由散發代理程式或記錄讀取器代理程式的狀態決定 (顯示較高優先權狀態；如果使用佇列更新訂閱，狀態也可以由佇列讀取器代理程式決定)。</span><span class="sxs-lookup"><span data-stu-id="40ce8-122">The status of each subscription, which is determined by the status of the Distribution Agent or the Log Reader Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span>  
  
 <span data-ttu-id="40ce8-123">依預設，包含訂閱資訊的方格是依 **[狀態]** 資料行排序 (然後由具有相同狀態之訂閱的 **[效能]** 資料行排序)。</span><span class="sxs-lookup"><span data-stu-id="40ce8-123">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="40ce8-124">下列清單顯示可能的狀態值和值的排序順序 (例如，錯誤一律顯示在方格頂端)。</span><span class="sxs-lookup"><span data-stu-id="40ce8-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="40ce8-125">錯誤</span><span class="sxs-lookup"><span data-stu-id="40ce8-125">Error</span></span>  
  
-   <span data-ttu-id="40ce8-126">效能嚴重不足</span><span class="sxs-lookup"><span data-stu-id="40ce8-126">Performance critical</span></span>  
  
-   <span data-ttu-id="40ce8-127">「即將過期/已過期」</span><span class="sxs-lookup"><span data-stu-id="40ce8-127">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="40ce8-128">未初始化的訂閱</span><span class="sxs-lookup"><span data-stu-id="40ce8-128">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="40ce8-129">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="40ce8-129">Retrying failed command</span></span>  
  
-   <span data-ttu-id="40ce8-130">未執行</span><span class="sxs-lookup"><span data-stu-id="40ce8-130">Not Running</span></span>  
  
-   <span data-ttu-id="40ce8-131">執行中</span><span class="sxs-lookup"><span data-stu-id="40ce8-131">Running</span></span>  
  
 <span data-ttu-id="40ce8-132">當給定訂閱有一個以上的狀態時，排序順序也會決定要顯示哪一個值。</span><span class="sxs-lookup"><span data-stu-id="40ce8-132">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="40ce8-133">例如，若訂閱有錯誤而且即將過期，則 **[狀態]** 資料行會顯示 **[錯誤]** 。</span><span class="sxs-lookup"><span data-stu-id="40ce8-133">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="40ce8-134">**[效能嚴重不足]** 、 **[即將過期/已過期]** 和 **[未初始化的訂閱]** 狀態值均為警告。</span><span class="sxs-lookup"><span data-stu-id="40ce8-134">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="40ce8-135">顯示警告時，如果代理程式正在執行，則 **[狀態]** 資料行也會顯示。</span><span class="sxs-lookup"><span data-stu-id="40ce8-135">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="40ce8-136">例如，狀態可能是 **[執行中，效能嚴重不足]** 。</span><span class="sxs-lookup"><span data-stu-id="40ce8-136">For example, the status could be **Running, Performance critical**.</span></span>  
  
 <span data-ttu-id="40ce8-137">唯有設定了臨界值，才會顯示狀態值 **[效能嚴重不足]** 和 **[即將過期/已過期]** 。</span><span class="sxs-lookup"><span data-stu-id="40ce8-137">The status values **Performance critical** and **Expiring soon/Expired** are displayed only if thresholds are set.</span></span> <span data-ttu-id="40ce8-138">如需效能測量和設定閾值的資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)和[在複寫監視器中設定閾值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="40ce8-138">For information about performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="40ce8-139">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="40ce8-139">**Subscription**</span></span>  
 <span data-ttu-id="40ce8-140">每一個訂閱的名稱，格式為： *SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="40ce8-140">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="40ce8-141">**發行集**</span><span class="sxs-lookup"><span data-stu-id="40ce8-141">**Publication**</span></span>  
 <span data-ttu-id="40ce8-142">與訂閱同步處理的發行集名稱，格式如下： *PublicationDatabaseName: PublicationName*。</span><span class="sxs-lookup"><span data-stu-id="40ce8-142">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="40ce8-143">**效能**</span><span class="sxs-lookup"><span data-stu-id="40ce8-143">**Performance**</span></span>  
 <span data-ttu-id="40ce8-144">每個訂閱的效能比是以複寫監視器進行的最近測量為基礎，且不會反映記錄效能。</span><span class="sxs-lookup"><span data-stu-id="40ce8-144">The performance rating for each subscription is based on the most recent measurements taken by Replication Monitor and does not reflect historical performance.</span></span> <span data-ttu-id="40ce8-145">會針對有定義效能臨界值的發行集訂閱，測量其效能；如果發行集沒有定義效能臨界值，此資料行就會顯示 **[未啟用]** 。</span><span class="sxs-lookup"><span data-stu-id="40ce8-145">Performance is measured for subscriptions to publications that have performance thresholds defined; if performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="40ce8-146">效能評比是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="40ce8-146">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="40ce8-147">非常好</span><span class="sxs-lookup"><span data-stu-id="40ce8-147">Excellent</span></span>  
  
-   <span data-ttu-id="40ce8-148">好</span><span class="sxs-lookup"><span data-stu-id="40ce8-148">Good</span></span>  
  
-   <span data-ttu-id="40ce8-149">普通</span><span class="sxs-lookup"><span data-stu-id="40ce8-149">Fair</span></span>  
  
-   <span data-ttu-id="40ce8-150">差</span><span class="sxs-lookup"><span data-stu-id="40ce8-150">Poor</span></span>  
  
-   <span data-ttu-id="40ce8-151">重大</span><span class="sxs-lookup"><span data-stu-id="40ce8-151">Critical</span></span>  
  
 <span data-ttu-id="40ce8-152">如果效能嚴重不足， **[狀態]** 資料行中就會顯示 **[效能嚴重不足]** 。</span><span class="sxs-lookup"><span data-stu-id="40ce8-152">If performance is critical, **Performance Critical** is displayed in the **Status** column.</span></span> <span data-ttu-id="40ce8-153">如需如何定義效能評比和如何設定效能閾值的詳細資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="40ce8-153">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="40ce8-154">**延遲**</span><span class="sxs-lookup"><span data-stu-id="40ce8-154">**Latency**</span></span>  
 <span data-ttu-id="40ce8-155">在發行者端認可之交易與在訂閱者端認可之對應交易之間經過的平均時間量。</span><span class="sxs-lookup"><span data-stu-id="40ce8-155">The average amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="40ce8-156">顯示的延遲是以複寫監視器進行的最近測量為基礎。</span><span class="sxs-lookup"><span data-stu-id="40ce8-156">The latency displayed is based on the most recent measurements taken by Replication Monitor.</span></span> <span data-ttu-id="40ce8-157">如需測量延遲的詳細資訊，請參閱[針對異動複寫測量延遲及驗證連線](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="40ce8-157">For more information about measuring latency, see [Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="40ce8-158">**上次同步處理日期**</span><span class="sxs-lookup"><span data-stu-id="40ce8-158">**Last Synchronization**</span></span>  
 <span data-ttu-id="40ce8-159">散發代理程式上次執行的時間。</span><span class="sxs-lookup"><span data-stu-id="40ce8-159">The time when the Distribution Agent last ran.</span></span> <span data-ttu-id="40ce8-160">如果正在進行同步處理，就會顯示 **[進行中]** 。</span><span class="sxs-lookup"><span data-stu-id="40ce8-160">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ce8-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40ce8-161">See Also</span></span>  
 <span data-ttu-id="40ce8-162">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="40ce8-162">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="40ce8-163">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="40ce8-163">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="40ce8-164">監視複寫</span><span class="sxs-lookup"><span data-stu-id="40ce8-164">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
