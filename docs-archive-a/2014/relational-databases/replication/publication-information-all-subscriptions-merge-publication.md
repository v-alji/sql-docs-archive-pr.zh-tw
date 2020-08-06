---
title: 發行集資訊，所有訂閱 (合併式發行集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.merge.f1
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 251e4c6e2e2adc60c838c7875d5d7d99aee64b54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708182"
---
# <a name="publication-information-all-subscriptions-merge-publication"></a><span data-ttu-id="7b835-102">發行集資訊，所有訂閱 (合併式發行集)</span><span class="sxs-lookup"><span data-stu-id="7b835-102">Publication Information, All Subscriptions (Merge Publication)</span></span>
  <span data-ttu-id="7b835-103"> [所有訂閱\]\*\*\** 索引標籤會顯示所選取合併式發行集之所有訂閱的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7b835-103">The **All Subscriptions** tab displays information on all subscriptions to the selected merge publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7b835-104">選項</span><span class="sxs-lookup"><span data-stu-id="7b835-104">Options</span></span>  
 <span data-ttu-id="7b835-105">如需詳細資訊以及與訂閱相關的工作，請以滑鼠右鍵按一下該訂閱的資料列，然後按一下捷徑功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="7b835-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="7b835-106">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="7b835-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="7b835-107">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="7b835-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="7b835-108">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="7b835-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="7b835-109">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="7b835-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="7b835-110">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="7b835-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="7b835-111">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="7b835-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="7b835-112">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="7b835-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="7b835-113">**顯示**</span><span class="sxs-lookup"><span data-stu-id="7b835-113">**Show**</span></span>  
 <span data-ttu-id="7b835-114">僅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="7b835-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="7b835-115">針對選取之訂閱類型，選取要顯示的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="7b835-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="7b835-116">例如，您可以選取只顯示有錯誤的訂閱。</span><span class="sxs-lookup"><span data-stu-id="7b835-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="7b835-117">**狀態**</span><span class="sxs-lookup"><span data-stu-id="7b835-117">**Status**</span></span>  
 <span data-ttu-id="7b835-118">每一個訂閱的狀態，是由合併代理程式的狀態決定。</span><span class="sxs-lookup"><span data-stu-id="7b835-118">The status of each subscription, which is determined by the status of the Merge Agent.</span></span>  
  
 <span data-ttu-id="7b835-119">依預設，包含訂閱資訊的方格是依 **[狀態]** 資料行排序 (然後由具有相同狀態之訂閱的 **[效能]** 資料行排序)。</span><span class="sxs-lookup"><span data-stu-id="7b835-119">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="7b835-120">下列清單顯示可能的狀態值和值的排序順序 (例如，錯誤一律顯示在方格頂端)。</span><span class="sxs-lookup"><span data-stu-id="7b835-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="7b835-121">錯誤</span><span class="sxs-lookup"><span data-stu-id="7b835-121">Error</span></span>  
  
-   <span data-ttu-id="7b835-122">效能嚴重不足 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="7b835-122">Performance critical ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="7b835-123">長期執行合併 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="7b835-123">Long-running merge ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="7b835-124">即將過期/已過期 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="7b835-124">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="7b835-125">未初始化的訂閱 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="7b835-125">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="7b835-126">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="7b835-126">Retrying failed command</span></span>  
  
-   <span data-ttu-id="7b835-127">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="7b835-127">Synchronizing</span></span>  
  
-   <span data-ttu-id="7b835-128">未進行同步處理</span><span class="sxs-lookup"><span data-stu-id="7b835-128">Not synchronizing</span></span>  
  
 <span data-ttu-id="7b835-129">當給定訂閱有一個以上的狀態時，排序順序也會決定要顯示哪一個值。</span><span class="sxs-lookup"><span data-stu-id="7b835-129">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="7b835-130">例如，若訂閱有錯誤而且即將過期，則 **[狀態]** 資料行會顯示 **[錯誤]**。</span><span class="sxs-lookup"><span data-stu-id="7b835-130">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="7b835-131">**[效能嚴重不足]**、 **[長時間執行的合併]**、 **[即將過期/已過期]** 和 **[未初始化的訂閱]** 等狀態值均為警告。</span><span class="sxs-lookup"><span data-stu-id="7b835-131">The status values **Performance critical**, **Long-running merge**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="7b835-132">如果有顯示警告，則 **[狀態]** 資料行也會顯示代理程式是否為同步處理。</span><span class="sxs-lookup"><span data-stu-id="7b835-132">When a warning is displayed, the **Status** column also displays if an agent is synchronizing.</span></span> <span data-ttu-id="7b835-133">例如，狀態可能是 **[正在同步處理，效能嚴重不足]**。</span><span class="sxs-lookup"><span data-stu-id="7b835-133">For example, the status could be **Synchronizing, Performance critical**.</span></span>  
  
 <span data-ttu-id="7b835-134">只有設定臨界值時，才會顯示 **[即將過期/已過期]** 和 **[長時間執行的合併]** 狀態值。</span><span class="sxs-lookup"><span data-stu-id="7b835-134">The status values **Expiring soon/Expired** and **Long-running merge** can be displayed only if thresholds are set.</span></span> <span data-ttu-id="7b835-135">只有在相同連接類型 (撥號或 LAN) 的訂閱經過五次同步處理之後，才會顯示 **[效能嚴重不足]** 的狀態值。</span><span class="sxs-lookup"><span data-stu-id="7b835-135">The status value **Performance critical** can be displayed only after five synchronizations of subscriptions with the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="7b835-136">如需效能測量和設定閾值的資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)和[在複寫監視器中設定閾值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="7b835-136">For information about performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="7b835-137">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="7b835-137">**Subscription**</span></span>  
 <span data-ttu-id="7b835-138">每一個訂閱名稱的格式為：*SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="7b835-138">The name of each subscription, in the form:*SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="7b835-139">**易記名稱**</span><span class="sxs-lookup"><span data-stu-id="7b835-139">**Friendly Name**</span></span>  
 <span data-ttu-id="7b835-140">僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="7b835-140">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="7b835-141">每一個訂閱的描述。</span><span class="sxs-lookup"><span data-stu-id="7b835-141">The description of each subscription.</span></span> <span data-ttu-id="7b835-142">此描述輸入於 **[訂閱屬性]** 對話方塊中，或以 **@description** 或 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) 的 [@description](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7b835-142">The description is entered in the **Subscription Properties** dialog box or specified with the **@description** parameter of [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) or [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="7b835-143">使用者通常使用描述作為訂閱的「易記名稱」或暱稱。</span><span class="sxs-lookup"><span data-stu-id="7b835-143">Users often use the description as a "friendly name" or nickname for the subscription.</span></span>  
  
 <span data-ttu-id="7b835-144">**效能**</span><span class="sxs-lookup"><span data-stu-id="7b835-144">**Performance**</span></span>  
 <span data-ttu-id="7b835-145">僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="7b835-145">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="7b835-146">每一個訂閱的效能評比，是以複寫監視器所測量之傳遞速率的最新數據為基礎。</span><span class="sxs-lookup"><span data-stu-id="7b835-146">The performance rating for each subscription, based on the most recent measurements of delivery rate taken by Replication Monitor.</span></span> <span data-ttu-id="7b835-147">評比會根據相同連接類型 (撥號或 LAN) 的發行集訂閱，進行個別訂閱效能和平均記錄效能的比較來決定。</span><span class="sxs-lookup"><span data-stu-id="7b835-147">The rating is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="7b835-148">在相同連接類型上發生過五次同步處理，且每次同步處理都具有 50 或更多個變更之後，複寫監視器才會顯示值。</span><span class="sxs-lookup"><span data-stu-id="7b835-148">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="7b835-149">如果具有 50 或更多個變更的同步處理少於五次，或者最近的同步處理少於 50 個變更，則此資料行為空白。</span><span class="sxs-lookup"><span data-stu-id="7b835-149">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b835-150">效能是以 **[連接]** 資料行所顯示的連接類型為基礎；因此，如果第一個訂閱是透過較慢速連接進行同步處理，則傳遞速率較低的訂閱有可能顯示比另一個訂閱更好的效能評比。</span><span class="sxs-lookup"><span data-stu-id="7b835-150">Performance is based on the connection type displayed in the **Connection** column; therefore it is possible for a subscription with a lower delivery rate to display a better performance rating than another subscription if the first subscription is synchronized over a slower connection.</span></span>  
  
 <span data-ttu-id="7b835-151">效能評比是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="7b835-151">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="7b835-152">非常好</span><span class="sxs-lookup"><span data-stu-id="7b835-152">Excellent</span></span>  
  
-   <span data-ttu-id="7b835-153">好</span><span class="sxs-lookup"><span data-stu-id="7b835-153">Good</span></span>  
  
-   <span data-ttu-id="7b835-154">普通</span><span class="sxs-lookup"><span data-stu-id="7b835-154">Fair</span></span>  
  
-   <span data-ttu-id="7b835-155">差</span><span class="sxs-lookup"><span data-stu-id="7b835-155">Poor</span></span>  
  
 <span data-ttu-id="7b835-156">如需如何定義效能評比和如何設定效能閾值的詳細資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="7b835-156">For more information on how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="7b835-157">**傳遞速率**</span><span class="sxs-lookup"><span data-stu-id="7b835-157">**Delivery Rate**</span></span>  
 <span data-ttu-id="7b835-158">合併代理程式每秒處理的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="7b835-158">The number of rows per second processed by the Merge Agent.</span></span>  
  
 <span data-ttu-id="7b835-159">**上次同步處理日期**</span><span class="sxs-lookup"><span data-stu-id="7b835-159">**Last Synchronization**</span></span>  
 <span data-ttu-id="7b835-160">合併代理程式上次執行的時間。</span><span class="sxs-lookup"><span data-stu-id="7b835-160">The time at which the Merge Agent last ran.</span></span> <span data-ttu-id="7b835-161">在這次同步處理期間不一定有處理變更。</span><span class="sxs-lookup"><span data-stu-id="7b835-161">Changes may or may not have been processed during this synchronization.</span></span> <span data-ttu-id="7b835-162">如果正在進行同步處理，就會顯示完成百分比值。</span><span class="sxs-lookup"><span data-stu-id="7b835-162">If synchronization is in progress, a percentage complete value is displayed.</span></span>  
  
 <span data-ttu-id="7b835-163">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="7b835-163">**Duration**</span></span>  
 <span data-ttu-id="7b835-164">合併代理程式在上次同步處理期間執行的時間量。</span><span class="sxs-lookup"><span data-stu-id="7b835-164">The amount of time the Merge Agent has run during the last synchronization.</span></span> <span data-ttu-id="7b835-165">如果合併代理程式目前正在進行同步處理，則時間代表經過時間，如果合併代理程式先前已同步處理，則時間代表總共花費的時間。</span><span class="sxs-lookup"><span data-stu-id="7b835-165">The time represents elapsed time if the Merge Agent is currently synchronizing and total time if the Merge Agent has synchronized previously.</span></span>  
  
 <span data-ttu-id="7b835-166">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="7b835-166">**Connection**</span></span>  
 <span data-ttu-id="7b835-167">僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="7b835-167">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="7b835-168">訂閱者和發行者之間的連接類型。</span><span class="sxs-lookup"><span data-stu-id="7b835-168">The type of connection between the Subscriber and the Publisher.</span></span> <span data-ttu-id="7b835-169">可能的值為 **[LAN]**、 **[撥號]** 和 **[網際網路]**。</span><span class="sxs-lookup"><span data-stu-id="7b835-169">The possible values are **LAN**, **Dialup**, and **Internet**.</span></span> <span data-ttu-id="7b835-170">如果訂閱使用 Web 同步處理，則會顯示 **[網際網路]** 值。</span><span class="sxs-lookup"><span data-stu-id="7b835-170">The **Internet** value is displayed if the subscription uses Web synchronization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b835-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b835-171">See Also</span></span>  
 <span data-ttu-id="7b835-172">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="7b835-172">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="7b835-173">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="7b835-173">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="7b835-174">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="7b835-174">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="7b835-175">合併式複寫的 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="7b835-175">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
