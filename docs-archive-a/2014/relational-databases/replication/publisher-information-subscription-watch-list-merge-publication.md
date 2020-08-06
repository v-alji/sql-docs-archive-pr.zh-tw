---
title: 發行者資訊、訂閱監看清單 (合併式發行集、SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.merge.f1
ms.assetid: 4ec956bf-5cef-4377-a1d1-8c7f0107a6cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cd38540533e3e663fa23eee2c651f0beb9463546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704997"
---
# <a name="publisher-information-subscription-watch-list-merge-publication-sql-server-2005-and-later"></a><span data-ttu-id="d68df-102">發行者資訊，訂閱監看清單 (合併式發行集，SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="d68df-102">Publisher Information, Subscription Watch List (Merge Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="d68df-103">執行 **和更新版本的散發者可以使用** [訂閱監看清單] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 索引標籤。這個索引標籤的用途是顯示選取發行者端之所有可用發行集的相關訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="d68df-103">The **Subscription Watch List** tab is available for Distributors running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="d68df-104">您可以篩選訂閱清單以查看錯誤、警告以及任何執行不良的訂閱。</span><span class="sxs-lookup"><span data-stu-id="d68df-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="d68df-105">此索引標籤為管理員提供監視發行者端所有複寫活動的單一位置：複寫監視器會根據選取的複寫類型和 **[顯示]** 下拉式清單方塊中選擇的選項，顯示需要注意的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="d68df-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="d68df-106">由於此索引標籤上顯示的項目會依據目前的狀態與效能，因此唯有在目前符合 **[顯示]** 清單方塊中之選項的訂閱，才會在這個頁面上顯示。</span><span class="sxs-lookup"><span data-stu-id="d68df-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d68df-107">選項</span><span class="sxs-lookup"><span data-stu-id="d68df-107">Options</span></span>  
 <span data-ttu-id="d68df-108">如需詳細資訊以及與訂閱相關的工作，請以滑鼠右鍵按一下該訂閱的資料列，然後按一下捷徑功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="d68df-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="d68df-109">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="d68df-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="d68df-110">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="d68df-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="d68df-111">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="d68df-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="d68df-112">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="d68df-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="d68df-113">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="d68df-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="d68df-114">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="d68df-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="d68df-115">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="d68df-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="d68df-116">**顯示合併訂閱**</span><span class="sxs-lookup"><span data-stu-id="d68df-116">**Show Merge Subscriptions**</span></span>  
 <span data-ttu-id="d68df-117">針對選取之發行者，選取要顯示的訂閱類型 (交易式、快照式或合併式)。</span><span class="sxs-lookup"><span data-stu-id="d68df-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="d68df-118">**顯示**</span><span class="sxs-lookup"><span data-stu-id="d68df-118">**Show**</span></span>  
 <span data-ttu-id="d68df-119">針對選取之訂閱類型，選取要顯示的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="d68df-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="d68df-120">例如，您可以選取只顯示有錯誤的訂閱。</span><span class="sxs-lookup"><span data-stu-id="d68df-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="d68df-121">**狀態**</span><span class="sxs-lookup"><span data-stu-id="d68df-121">**Status**</span></span>  
 <span data-ttu-id="d68df-122">每一個訂閱的狀態，是由合併代理程式的狀態決定。</span><span class="sxs-lookup"><span data-stu-id="d68df-122">The status of each subscription, which is determined by the status of the Merge Agent.</span></span>  
  
 <span data-ttu-id="d68df-123">依預設，包含訂閱資訊的方格是依 **[狀態]** 資料行排序 (然後由具有相同狀態之訂閱的 **[效能]** 資料行排序)。</span><span class="sxs-lookup"><span data-stu-id="d68df-123">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="d68df-124">下列清單顯示可能的狀態值和值的排序順序 (例如，錯誤一律顯示在方格頂端)。</span><span class="sxs-lookup"><span data-stu-id="d68df-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="d68df-125">錯誤</span><span class="sxs-lookup"><span data-stu-id="d68df-125">Error</span></span>  
  
-   <span data-ttu-id="d68df-126">效能嚴重不足</span><span class="sxs-lookup"><span data-stu-id="d68df-126">Performance critical</span></span>  
  
-   <span data-ttu-id="d68df-127">長期執行合併</span><span class="sxs-lookup"><span data-stu-id="d68df-127">Long-running merge</span></span>  
  
-   <span data-ttu-id="d68df-128">「即將過期/已過期」</span><span class="sxs-lookup"><span data-stu-id="d68df-128">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="d68df-129">未初始化的訂閱</span><span class="sxs-lookup"><span data-stu-id="d68df-129">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="d68df-130">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="d68df-130">Retrying failed command</span></span>  
  
-   <span data-ttu-id="d68df-131">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="d68df-131">Synchronizing</span></span>  
  
-   <span data-ttu-id="d68df-132">未進行同步處理</span><span class="sxs-lookup"><span data-stu-id="d68df-132">Not synchronizing</span></span>  
  
 <span data-ttu-id="d68df-133">當給定訂閱有一個以上的狀態時，排序順序也會決定要顯示哪一個值。</span><span class="sxs-lookup"><span data-stu-id="d68df-133">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="d68df-134">例如，若訂閱有錯誤而且即將過期，則 **[狀態]** 資料行會顯示 **[錯誤]**。</span><span class="sxs-lookup"><span data-stu-id="d68df-134">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="d68df-135">**[效能嚴重不足]**、 **[長時間執行的合併]**、 **[即將過期/已過期]** 和 **[未初始化的訂閱]** 等狀態值均為警告。</span><span class="sxs-lookup"><span data-stu-id="d68df-135">The status values **Performance critical**, **Long-running merge**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="d68df-136">如果有顯示警告，則 **[狀態]** 資料行也會顯示代理程式是否為同步處理。</span><span class="sxs-lookup"><span data-stu-id="d68df-136">When a warning is displayed, the **Status** column also displays if an agent is synchronizing.</span></span> <span data-ttu-id="d68df-137">例如，狀態可能是 **[正在同步處理，效能嚴重不足]**。</span><span class="sxs-lookup"><span data-stu-id="d68df-137">For example, the status could be **Synchronizing, Performance critical**.</span></span>  
  
 <span data-ttu-id="d68df-138">只有設定臨界值時，才會顯示 **[即將過期/已過期]** 和 **[長時間執行的合併]** 狀態值。</span><span class="sxs-lookup"><span data-stu-id="d68df-138">The status values **Expiring soon/Expired** and **Long-running merge** can be displayed only if thresholds are set.</span></span> <span data-ttu-id="d68df-139">只有在相同連接類型 (撥號或 LAN) 的訂閱經過五次同步處理之後，才會顯示 **[效能嚴重不足]** 的狀態值。</span><span class="sxs-lookup"><span data-stu-id="d68df-139">The status value **Performance critical** can be displayed only after five synchronizations of subscriptions with the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="d68df-140">如需效能測量和設定閾值的資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)和[在複寫監視器中設定閾值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d68df-140">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="d68df-141">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="d68df-141">**Subscription**</span></span>  
 <span data-ttu-id="d68df-142">每一個訂閱名稱的格式為：*SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="d68df-142">The name of each subscription, in the form:*SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="d68df-143">**易記名稱**</span><span class="sxs-lookup"><span data-stu-id="d68df-143">**Friendly Name**</span></span>  
 <span data-ttu-id="d68df-144">每一個訂閱的描述。</span><span class="sxs-lookup"><span data-stu-id="d68df-144">The description of each subscription.</span></span> <span data-ttu-id="d68df-145">此描述輸入於 **[訂閱屬性]** 對話方塊中，或以 **@description** 或 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) 的 [@description](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d68df-145">The description is entered in the **Subscription Properties** dialog box or specified with the **@description** parameter of [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) or [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="d68df-146">使用者通常使用描述作為訂閱的「易記名稱」或暱稱。</span><span class="sxs-lookup"><span data-stu-id="d68df-146">Users often use the description as a "friendly name" or nickname for the subscription.</span></span>  
  
 <span data-ttu-id="d68df-147">**發行**</span><span class="sxs-lookup"><span data-stu-id="d68df-147">**Publication**</span></span>  
 <span data-ttu-id="d68df-148">與訂閱同步處理的發行集名稱，格式如下： *PublicationDatabaseName: PublicationName*。</span><span class="sxs-lookup"><span data-stu-id="d68df-148">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="d68df-149">**效能**</span><span class="sxs-lookup"><span data-stu-id="d68df-149">**Performance**</span></span>  
 <span data-ttu-id="d68df-150">每一個訂閱的效能評比，是以複寫監視器所測量之傳遞速率的最新數據為基礎。</span><span class="sxs-lookup"><span data-stu-id="d68df-150">The performance rating for each subscription, based on the most recent measurements of delivery rate taken by Replication Monitor.</span></span> <span data-ttu-id="d68df-151">評比會根據相同連接類型 (撥號或 LAN) 的發行集訂閱，進行個別訂閱效能和平均記錄效能的比較來決定。</span><span class="sxs-lookup"><span data-stu-id="d68df-151">The rating is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="d68df-152">在相同連接類型上發生過五次同步處理，且每次同步處理都具有 50 或更多個變更之後，複寫監視器才會顯示值。</span><span class="sxs-lookup"><span data-stu-id="d68df-152">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="d68df-153">如果具有 50 或更多個變更的同步處理少於五次，或者最近的同步處理少於 50 個變更，則此資料行為空白。</span><span class="sxs-lookup"><span data-stu-id="d68df-153">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d68df-154">效能是以 **[連接]** 資料行所顯示的連接類型為基礎；因此，如果第一個訂閱是透過較慢速連接進行同步處理，則傳遞速率較低的訂閱有可能顯示比另一個訂閱更好的效能評比。</span><span class="sxs-lookup"><span data-stu-id="d68df-154">Performance is based on the connection type displayed in the **Connection** column; therefore it is possible for a subscription with a lower delivery rate to display a better performance rating than another subscription if the first subscription is synchronized over a slower connection.</span></span>  
  
 <span data-ttu-id="d68df-155">效能評比是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="d68df-155">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="d68df-156">非常好</span><span class="sxs-lookup"><span data-stu-id="d68df-156">Excellent</span></span>  
  
-   <span data-ttu-id="d68df-157">好</span><span class="sxs-lookup"><span data-stu-id="d68df-157">Good</span></span>  
  
-   <span data-ttu-id="d68df-158">普通</span><span class="sxs-lookup"><span data-stu-id="d68df-158">Fair</span></span>  
  
-   <span data-ttu-id="d68df-159">差</span><span class="sxs-lookup"><span data-stu-id="d68df-159">Poor</span></span>  
  
 <span data-ttu-id="d68df-160">如需如何定義效能評比和如何設定效能閾值的詳細資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d68df-160">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="d68df-161">**傳遞速率**</span><span class="sxs-lookup"><span data-stu-id="d68df-161">**Delivery Rate**</span></span>  
 <span data-ttu-id="d68df-162">合併代理程式每秒處理的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d68df-162">The number of rows per second processed by the Merge Agent.</span></span>  
  
 <span data-ttu-id="d68df-163">**上次同步處理日期**</span><span class="sxs-lookup"><span data-stu-id="d68df-163">**Last Synchronization**</span></span>  
 <span data-ttu-id="d68df-164">合併代理程式上次執行的時間。</span><span class="sxs-lookup"><span data-stu-id="d68df-164">The time at which the Merge Agent last ran.</span></span> <span data-ttu-id="d68df-165">在這次同步處理期間不一定有處理變更。</span><span class="sxs-lookup"><span data-stu-id="d68df-165">Changes may or may not have been processed during this synchronization.</span></span> <span data-ttu-id="d68df-166">如果正在進行同步處理，就會顯示完成百分比值。</span><span class="sxs-lookup"><span data-stu-id="d68df-166">If synchronization is in progress, a percentage complete value is displayed.</span></span>  
  
 <span data-ttu-id="d68df-167">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="d68df-167">**Duration**</span></span>  
 <span data-ttu-id="d68df-168">合併代理程式在上次同步處理期間執行的時間量。</span><span class="sxs-lookup"><span data-stu-id="d68df-168">The amount of time the Merge Agent has run during the last synchronization.</span></span> <span data-ttu-id="d68df-169">如果合併代理程式目前正在進行同步處理，則時間代表經過時間，如果合併代理程式先前已同步處理，則時間代表總共花費的時間。</span><span class="sxs-lookup"><span data-stu-id="d68df-169">The time represents elapsed time if the Merge Agent is currently synchronizing and total time if the Merge Agent has synchronized previously.</span></span>  
  
 <span data-ttu-id="d68df-170">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="d68df-170">**Connection**</span></span>  
 <span data-ttu-id="d68df-171">訂閱者和發行者之間的連接類型。</span><span class="sxs-lookup"><span data-stu-id="d68df-171">The type of connection between the Subscriber and the Publisher.</span></span> <span data-ttu-id="d68df-172">可能的值為 **[LAN]**、 **[撥號]** 和 **[網際網路]**。</span><span class="sxs-lookup"><span data-stu-id="d68df-172">The possible values are **LAN**, **Dialup**, and **Internet**.</span></span> <span data-ttu-id="d68df-173">如果訂閱使用 Web 同步處理，則會顯示 **[網際網路]** 值。</span><span class="sxs-lookup"><span data-stu-id="d68df-173">The **Internet** value is displayed if the subscription uses Web synchronization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68df-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d68df-174">See Also</span></span>  
 <span data-ttu-id="d68df-175">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d68df-175">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="d68df-176">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d68df-176">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="d68df-177">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="d68df-177">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="d68df-178">合併式複寫的 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="d68df-178">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
