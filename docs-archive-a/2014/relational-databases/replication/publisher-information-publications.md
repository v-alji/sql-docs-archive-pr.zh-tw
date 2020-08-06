---
title: SQL Server 複寫 [發行者資訊] 對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.publications.f1
ms.assetid: 0b2e3d4e-03b7-4c31-8f96-48648d750010
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3797ae4f9fe8f42b4abec715c63bc627c2a62cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697888"
---
# <a name="sql-server-replication-publisher-information-dialog-box"></a><span data-ttu-id="bccad-102">SQL Server 複寫 [發行者資訊] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="bccad-102">SQL Server Replication 'Publisher Information' dialog box</span></span>
  <span data-ttu-id="bccad-103">**[發行集]** 索引標籤可以提供在左窗格中所選取發行者之所有發行集的摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="bccad-103">The **Publications** tab provides summary information for all publications at the Publisher selected in the left pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bccad-104">選項。</span><span class="sxs-lookup"><span data-stu-id="bccad-104">Options</span></span>  
 <span data-ttu-id="bccad-105">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="bccad-105">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="bccad-106">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="bccad-106">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="bccad-107">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="bccad-107">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="bccad-108">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="bccad-108">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="bccad-109">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="bccad-109">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="bccad-110">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="bccad-110">Filter settings are specific to each grid.</span></span> <span data-ttu-id="bccad-111">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="bccad-111">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="bccad-112">**狀態**</span><span class="sxs-lookup"><span data-stu-id="bccad-112">**Status**</span></span>  
 <span data-ttu-id="bccad-113">每一個發行集的狀態，由訂閱的最高優先權狀態來決定。</span><span class="sxs-lookup"><span data-stu-id="bccad-113">The status of each publication, which is determined by the highest priority status of its subscriptions.</span></span> <span data-ttu-id="bccad-114">依預設，包含發行集資訊的方格會依 **[狀態]** 資料行排序。</span><span class="sxs-lookup"><span data-stu-id="bccad-114">By default, the grid containing publication information is sorted by the **Status** column.</span></span> <span data-ttu-id="bccad-115">下列清單會顯示可能的狀態值，以及值的排序順序 (例如，錯誤會一律顯示在方格頂端)：</span><span class="sxs-lookup"><span data-stu-id="bccad-115">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid):</span></span>  
  
-   <span data-ttu-id="bccad-116">錯誤</span><span class="sxs-lookup"><span data-stu-id="bccad-116">Error</span></span>  
  
-   <span data-ttu-id="bccad-117">效能嚴重不足</span><span class="sxs-lookup"><span data-stu-id="bccad-117">Performance critical</span></span>  
  
-   <span data-ttu-id="bccad-118">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="bccad-118">Retrying failed command</span></span>  
  
-   <span data-ttu-id="bccad-119">[確定]</span><span class="sxs-lookup"><span data-stu-id="bccad-119">OK</span></span>  
  
 <span data-ttu-id="bccad-120">**[效能嚴重不足]** 狀態值與交易式訂閱和合併訂閱有關；對交易式訂閱而言，唯有已設定臨界值時，才會顯示此狀態值。</span><span class="sxs-lookup"><span data-stu-id="bccad-120">The status value **Performance critical** is relevant for transactional subscriptions and merge subscriptions; for transactional subscriptions, it can be displayed only if a threshold is set.</span></span> <span data-ttu-id="bccad-121">如需效能測量和設定閾值的資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)和[在複寫監視器中設定閾值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="bccad-121">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="bccad-122">**發行集**</span><span class="sxs-lookup"><span data-stu-id="bccad-122">**Publication**</span></span>  
 <span data-ttu-id="bccad-123">每個發行集的名稱，格式為 *PublicationDatabaseName: PublicationName*。</span><span class="sxs-lookup"><span data-stu-id="bccad-123">The name of each publication, in the form *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="bccad-124">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="bccad-124">**Subscriptions**</span></span>  
 <span data-ttu-id="bccad-125">每一個發行集的訂閱數目。</span><span class="sxs-lookup"><span data-stu-id="bccad-125">The number of subscriptions for each publication.</span></span>  
  
 <span data-ttu-id="bccad-126">**正在同步處理**</span><span class="sxs-lookup"><span data-stu-id="bccad-126">**Synchronizing**</span></span>  
 <span data-ttu-id="bccad-127">目前正在進行同步處理之每一個發行集的訂閱數目：</span><span class="sxs-lookup"><span data-stu-id="bccad-127">The number of subscriptions for each publication that are currently synchronizing:</span></span>  
  
-   <span data-ttu-id="bccad-128">對異動複寫而言，「正在同步處理」表示散發代理程式正在執行，但不一定正在複寫資料。</span><span class="sxs-lookup"><span data-stu-id="bccad-128">For transactional replication, "synchronizing" means that the Distribution Agent is running, but data is not necessarily being replicated.</span></span>  
  
-   <span data-ttu-id="bccad-129">對合併式複寫而言，「正在同步處理」表示全併代理程式正在執行，且目前正在複寫資料。</span><span class="sxs-lookup"><span data-stu-id="bccad-129">For merge replication, "synchronizing" means that the Merge Agent is running and that data is currently being replicated.</span></span>  
  
-   <span data-ttu-id="bccad-130">對快照式複寫而言，「正在同步處理」表示散發代理程式正在執行，且目前正在複寫資料。</span><span class="sxs-lookup"><span data-stu-id="bccad-130">For snapshot replication, "synchronizing" means that the Distribution Agent is running and that data is currently being replicated.</span></span>  
  
 <span data-ttu-id="bccad-131">**目前的平均效能** 和 **目前最差效能**</span><span class="sxs-lookup"><span data-stu-id="bccad-131">**Current Average Performance** and **Current Worst Performance**</span></span>  
 <span data-ttu-id="bccad-132">僅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="bccad-132">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="bccad-133">分別代表發行集之所有訂閱的平均效能評比和最差效能評比。</span><span class="sxs-lookup"><span data-stu-id="bccad-133">The average performance rating and the worst performance rating, respectively, for all subscriptions to a publication.</span></span> <span data-ttu-id="bccad-134">評比是以複寫監視器最近使用的度量單位為基礎，並不反映訂閱經過一段時間的效能。</span><span class="sxs-lookup"><span data-stu-id="bccad-134">Ratings are based on the most recent measurements taken by Replication Monitor and do not reflect the performance of a subscription over time.</span></span>  
  
 <span data-ttu-id="bccad-135">對異動複寫而言，複寫監視器只會顯示已定義效能臨界值之發行集的值。</span><span class="sxs-lookup"><span data-stu-id="bccad-135">For transactional replication, Replication Monitor displays a value only for publications that have performance thresholds defined.</span></span> <span data-ttu-id="bccad-136">如果發行集未定義效能臨界值，則此資料行會顯示 **[未啟用]** 。</span><span class="sxs-lookup"><span data-stu-id="bccad-136">If performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="bccad-137">對合併式複寫而言，在相同連接類型 (撥號或 LAN) 上發生過五次同步處理，且每次同步處理都具有 50 或更多個變更之後，複寫監視器才會顯示值。</span><span class="sxs-lookup"><span data-stu-id="bccad-137">For merge replication, Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection (dial-up or LAN).</span></span> <span data-ttu-id="bccad-138">如果具有 50 或更多個變更的同步處理少於五次，或者最近的同步處理少於 50 個變更，則此資料行為空白。</span><span class="sxs-lookup"><span data-stu-id="bccad-138">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
 <span data-ttu-id="bccad-139">效能評比是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="bccad-139">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="bccad-140">非常好</span><span class="sxs-lookup"><span data-stu-id="bccad-140">Excellent</span></span>  
  
-   <span data-ttu-id="bccad-141">好</span><span class="sxs-lookup"><span data-stu-id="bccad-141">Good</span></span>  
  
-   <span data-ttu-id="bccad-142">普通</span><span class="sxs-lookup"><span data-stu-id="bccad-142">Fair</span></span>  
  
-   <span data-ttu-id="bccad-143">差</span><span class="sxs-lookup"><span data-stu-id="bccad-143">Poor</span></span>  
  
-   <span data-ttu-id="bccad-144">重大</span><span class="sxs-lookup"><span data-stu-id="bccad-144">Critical</span></span>  
  
 <span data-ttu-id="bccad-145">如需如何定義效能評比和如何設定效能閾值的詳細資訊，請參閱[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="bccad-145">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccad-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bccad-146">See Also</span></span>  
 <span data-ttu-id="bccad-147">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="bccad-147">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="bccad-148">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="bccad-148">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="bccad-149">監視複寫</span><span class="sxs-lookup"><span data-stu-id="bccad-149">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
