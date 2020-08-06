---
title: 發行集資訊，所有訂閱 (交易式發行集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.tran.f1
ms.assetid: 7073350c-f667-4f70-88e9-152c9a1b08dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccc34bbe0933f4558478bd1d8276898219016e24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592628"
---
# <a name="publication-information-all-subscriptions-transactional-publication"></a><span data-ttu-id="3830a-102">發行集資訊，所有訂閱 (交易式發行集)</span><span class="sxs-lookup"><span data-stu-id="3830a-102">Publication Information, All Subscriptions (Transactional Publication)</span></span>
  <span data-ttu-id="3830a-103">**[所有訂閱]** 索引標籤會針對選取之交易式發行集的所有訂閱顯示其資訊。</span><span class="sxs-lookup"><span data-stu-id="3830a-103">The **All Subscriptions** tab displays information on all subscriptions to the selected transactional publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3830a-104">選項</span><span class="sxs-lookup"><span data-stu-id="3830a-104">Options</span></span>  
 <span data-ttu-id="3830a-105">如需詳細資訊以及與訂閱相關的工作，請以滑鼠右鍵按一下該訂閱的資料列，然後按一下捷徑功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="3830a-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="3830a-106">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="3830a-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="3830a-107">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="3830a-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="3830a-108">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="3830a-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="3830a-109">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="3830a-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="3830a-110">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="3830a-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="3830a-111">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="3830a-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="3830a-112">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="3830a-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="3830a-113">**顯示**</span><span class="sxs-lookup"><span data-stu-id="3830a-113">**Show**</span></span>  
 <span data-ttu-id="3830a-114">僅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="3830a-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="3830a-115">針對選取之訂閱類型，選取要顯示的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="3830a-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="3830a-116">例如，您可以選取只顯示有錯誤的訂閱。</span><span class="sxs-lookup"><span data-stu-id="3830a-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="3830a-117">**狀態**</span><span class="sxs-lookup"><span data-stu-id="3830a-117">**Status**</span></span>  
 <span data-ttu-id="3830a-118">每個訂閱的狀態，這是由散發代理程式或記錄讀取器代理程式的狀態決定 (顯示較高優先權狀態；如果使用佇列更新訂閱，狀態也可以由佇列讀取器代理程式決定)。</span><span class="sxs-lookup"><span data-stu-id="3830a-118">The status of each subscription, which is determined by the status of the Distribution Agent or the Log Reader Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span>  
  
 <span data-ttu-id="3830a-119">依預設，包含訂閱資訊的方格是依 **[狀態]** 資料行排序 (然後由具有相同狀態之訂閱的 **[效能]** 資料行排序)。</span><span class="sxs-lookup"><span data-stu-id="3830a-119">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="3830a-120">下列清單顯示可能的狀態值和值的排序順序 (例如，錯誤一律顯示在方格頂端)。</span><span class="sxs-lookup"><span data-stu-id="3830a-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="3830a-121">錯誤</span><span class="sxs-lookup"><span data-stu-id="3830a-121">Error</span></span>  
  
-   <span data-ttu-id="3830a-122">效能嚴重不足 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="3830a-122">Performance critical ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="3830a-123">即將過期/已過期 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="3830a-123">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="3830a-124">未初始化的訂閱 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="3830a-124">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="3830a-125">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="3830a-125">Retrying failed command</span></span>  
  
-   <span data-ttu-id="3830a-126">未執行</span><span class="sxs-lookup"><span data-stu-id="3830a-126">Not Running</span></span>  
  
-   <span data-ttu-id="3830a-127">執行中</span><span class="sxs-lookup"><span data-stu-id="3830a-127">Running</span></span>  
  
 <span data-ttu-id="3830a-128">當給定訂閱有一個以上的狀態時，排序順序也會決定要顯示哪一個值。</span><span class="sxs-lookup"><span data-stu-id="3830a-128">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="3830a-129">例如，若訂閱有錯誤而且即將過期，則 **[狀態]** 資料行會顯示 **[錯誤]**。</span><span class="sxs-lookup"><span data-stu-id="3830a-129">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="3830a-130">**[效能嚴重不足]**、 **[即將過期/已過期]** 和 **[未初始化的訂閱]** 狀態值均為警告。</span><span class="sxs-lookup"><span data-stu-id="3830a-130">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="3830a-131">顯示警告時，如果代理程式正在執行，則 **[狀態]** 資料行也會顯示。</span><span class="sxs-lookup"><span data-stu-id="3830a-131">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="3830a-132">例如，狀態可能是 **[執行中，效能嚴重不足]**。</span><span class="sxs-lookup"><span data-stu-id="3830a-132">For example, the status could be **Running, Performance critical**.</span></span>  
  
 <span data-ttu-id="3830a-133">唯有設定了臨界值，才會顯示狀態值 **[效能嚴重不足]** 和 **[即將過期/已過期]** 。</span><span class="sxs-lookup"><span data-stu-id="3830a-133">The status values **Performance critical** and **Expiring soon/Expired** are displayed only if thresholds are set.</span></span> <span data-ttu-id="3830a-134">如需效能測量和設定閾值的資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)和[在複寫監視器中設定閾值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3830a-134">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="3830a-135">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="3830a-135">**Subscription**</span></span>  
 <span data-ttu-id="3830a-136">每一個訂閱的名稱，格式為： *SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="3830a-136">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="3830a-137">**效能**</span><span class="sxs-lookup"><span data-stu-id="3830a-137">**Performance**</span></span>  
 <span data-ttu-id="3830a-138">僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="3830a-138">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="3830a-139">每個訂閱的效能比是以複寫監視器進行的最近測量為基礎，且不會反映記錄效能。</span><span class="sxs-lookup"><span data-stu-id="3830a-139">The performance rating for each subscription is based on the most recent measurements taken by Replication Monitor and does not reflect historical performance.</span></span> <span data-ttu-id="3830a-140">會針對有定義效能臨界值的發行集訂閱，測量其效能；如果發行集沒有定義效能臨界值，此資料行就會顯示 **[未啟用]**。</span><span class="sxs-lookup"><span data-stu-id="3830a-140">Performance is measured for subscriptions to publications that have performance thresholds defined; if performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="3830a-141">效能評比是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="3830a-141">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="3830a-142">非常好</span><span class="sxs-lookup"><span data-stu-id="3830a-142">Excellent</span></span>  
  
-   <span data-ttu-id="3830a-143">好</span><span class="sxs-lookup"><span data-stu-id="3830a-143">Good</span></span>  
  
-   <span data-ttu-id="3830a-144">普通</span><span class="sxs-lookup"><span data-stu-id="3830a-144">Fair</span></span>  
  
-   <span data-ttu-id="3830a-145">差</span><span class="sxs-lookup"><span data-stu-id="3830a-145">Poor</span></span>  
  
-   <span data-ttu-id="3830a-146">重要</span><span class="sxs-lookup"><span data-stu-id="3830a-146">Critical</span></span>  
  
 <span data-ttu-id="3830a-147">如果效能嚴重不足， **[狀態]** 資料行中就會顯示 **[效能嚴重不足]** 。</span><span class="sxs-lookup"><span data-stu-id="3830a-147">If performance is critical, **Performance Critical** is displayed in the **Status** column.</span></span> <span data-ttu-id="3830a-148">如需如何定義效能評比和如何設定效能閾值的詳細資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3830a-148">For more information on how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="3830a-149">**延遲**</span><span class="sxs-lookup"><span data-stu-id="3830a-149">**Latency**</span></span>  
 <span data-ttu-id="3830a-150">僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="3830a-150">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="3830a-151">在發行者端認可之交易與在訂閱者端認可之對應交易之間經過的平均時間量。</span><span class="sxs-lookup"><span data-stu-id="3830a-151">The average amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="3830a-152">顯示的延遲是以複寫監視器進行的最近測量為基礎。</span><span class="sxs-lookup"><span data-stu-id="3830a-152">The latency displayed is based on the most recent measurements taken by Replication Monitor.</span></span> <span data-ttu-id="3830a-153">如需測量延遲的詳細資訊，請參閱[針對異動複寫測量延遲及驗證連線](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="3830a-153">For more information about measuring latency, see [Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3830a-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3830a-154">See Also</span></span>  
 <span data-ttu-id="3830a-155">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3830a-155">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="3830a-156">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3830a-156">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="3830a-157">監視複寫</span><span class="sxs-lookup"><span data-stu-id="3830a-157">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
