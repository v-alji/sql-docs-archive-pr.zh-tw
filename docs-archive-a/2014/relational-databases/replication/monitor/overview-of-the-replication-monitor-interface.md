---
title: 複寫監視器介面概觀 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 078f0e34-7153-45c4-8725-778b5bef88da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d9b7edbd76153f23168ec9bcf4a286d5f7cbe9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593934"
---
# <a name="overview-of-the-replication-monitor-interface"></a><span data-ttu-id="d4aa0-102">複寫監視器介面概觀</span><span class="sxs-lookup"><span data-stu-id="d4aa0-102">Overview of the Replication Monitor Interface</span></span>
  <span data-ttu-id="d4aa0-103">「[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫監視器」以兩個窗格來針對所有複寫活動呈現以「發行者」或「散發者」為焦點的檢視。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor presents a Publisher-focused view or Distributor-focused view of all replication activity in a two pane format.</span></span> <span data-ttu-id="d4aa0-104">您可將發行者加入監視器的左窗格中，監視器的右窗格便會顯示關於發行者及其發行集、這些發行集的訂閱，以及各種複寫代理程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-104">You add a Publisher to the monitor in the left pane, and in the right pane the monitor displays information on the Publisher, its publications, the subscriptions to those publications, and the various replication agents.</span></span> <span data-ttu-id="d4aa0-105">除了呈現複寫拓撲的資訊外，「複寫監視器」還可讓您執行一些工作，例如啟動和停止代理程式，以及驗證資料。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-105">In addition to presenting information for the replication topology, Replication Monitor allows you to perform a number of tasks, such as starting and stopping agents, and validating data.</span></span>  
  
## <a name="viewing-information-for-the-entire-topology"></a><span data-ttu-id="d4aa0-106">檢視整個拓撲的資訊</span><span class="sxs-lookup"><span data-stu-id="d4aa0-106">Viewing Information for the Entire Topology</span></span>  
 <span data-ttu-id="d4aa0-107">複寫監視器左邊的窗格會顯示</span><span class="sxs-lookup"><span data-stu-id="d4aa0-107">The left pane of Replication Monitor displays</span></span>  
  
-   <span data-ttu-id="d4aa0-108">發行者群組、發行者和發行集。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-108">Publisher groups, Publishers, and publications.</span></span>  
  
-   <span data-ttu-id="d4aa0-109">散發者、發行者和發行集。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-109">Distributors, Publishers, and publications.</span></span>  
  
 <span data-ttu-id="d4aa0-110">若要在「複寫監視器」中檢視任何資訊，必須先加入發行者。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-110">To view any information in Replication Monitor, you must first add a Publisher.</span></span> <span data-ttu-id="d4aa0-111">如需詳細資訊，請參閱 [從複寫監視器加入及移除發行者](add-and-remove-publishers-from-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-111">For more information, see [Add and Remove Publishers from Replication Monitor](add-and-remove-publishers-from-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="d4aa0-112">左窗格可協助回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-112">The left pane helps answer the following questions:</span></span>  
  
-   <span data-ttu-id="d4aa0-113">我的複寫系統狀況是否良好？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-113">Is my replication system healthy?</span></span>  
  
     <span data-ttu-id="d4aa0-114">如果左窗格中的節點上沒有錯誤圖示，則複寫系統的狀況相對健全。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-114">The replication system is relatively healthy if there are no error icons on nodes in the left pane.</span></span> <span data-ttu-id="d4aa0-115">若要取得更完整的系統健全狀況檢視，您也應該檢查 **[訂閱監看清單]** 索引標籤，其中會顯示可能需要注意的訂閱之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-115">To get a more complete view of system health, you should also check the **Subscription Watch List** tab, which displays information on subscriptions that might require attention.</span></span>  
  
-   <span data-ttu-id="d4aa0-116">代理程式為何沒有執行？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-116">Why is an agent not running?</span></span>  
  
     <span data-ttu-id="d4aa0-117">如果代理程式沒有在特定時間執行，可能是因為並未排程執行或是已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-117">An agent is not running at a particular time either because it is not scheduled to run or because an error has occurred.</span></span> <span data-ttu-id="d4aa0-118">如果發生錯誤，左窗格中的適當節點上會顯示錯誤圖示。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-118">If an error has occurred, an error icon is displayed on the appropriate nodes in the left pane.</span></span> <span data-ttu-id="d4aa0-119">例如，如果發行集的「快照集代理程式」因錯誤而停止，則發行者群組、發行者和發行集節點上會顯示錯誤圖示。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-119">For example, if the Snapshot Agent for a publication stopped because of an error, an error icon is displayed on the Publisher group, Publisher, and publication nodes.</span></span> <span data-ttu-id="d4aa0-120">「快照集代理程式」的摘要資訊會顯示在發行集的 **[代理程式]** 索引標籤上；按兩下此索引標籤上的「快照集代理程式」可取得詳細的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-120">Summary information for the Snapshot Agent is displayed on the **Agents** tab for the publication; double click the Snapshot Agent on this tab for detailed error information.</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-distributors"></a><span data-ttu-id="d4aa0-121">檢視與散發者相關的資訊並執行工作</span><span class="sxs-lookup"><span data-stu-id="d4aa0-121">Viewing Information and Performing Tasks Related to Distributors</span></span>  
 <span data-ttu-id="d4aa0-122">「複寫監視器」會在下列三個索引標籤上顯示散發者的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-122">Replication Monitor displays information about Distributors on three tabs:</span></span>  
  
-   <span data-ttu-id="d4aa0-123">**[發行集]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-123">**Publications** tab</span></span>  
  
     <span data-ttu-id="d4aa0-124">此索引標籤提供散發者所有發行集的摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-124">This tab provides summary information for all publications of a Distributor.</span></span>  
  
-   <span data-ttu-id="d4aa0-125">**[訂閱監看清單]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-125">**Subscription Watch List** tab</span></span>  
  
     <span data-ttu-id="d4aa0-126">這個索引標籤會提供有關選取之散發者的所有訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-126">This tab provides information about subscriptions for the selected Distributor.</span></span> <span data-ttu-id="d4aa0-127">您可以篩選訂閱清單以查看錯誤、警告以及任何執行不良的訂閱。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-127">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="d4aa0-128">此索引標籤也可讓您執行下列工作：存取訂閱屬性、存取與訂閱相關聯的一個或多個代理程式之詳細資訊、重新初始化訂閱，以及驗證訂閱。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-128">The tab also lets you to perform the following tasks: access subscription properties, access detailed information about the agent or agents associated with a subscription, reinitialize subscriptions, and validate subscriptions.</span></span>  
  
     <span data-ttu-id="d4aa0-129">**[訂閱監看清單]** 索引標籤可協助回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-129">The **Subscription Watch List** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="d4aa0-130">哪些訂閱的速度慢？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-130">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="d4aa0-131">設定這個索引標籤上的選項，使方格依相關效能的順序顯示訂閱。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-131">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="d4aa0-132">我的複寫系統狀況是否良好？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-132">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="d4aa0-133">這個索引標籤上的方格會顯示需要您注意之任何訂閱的錯誤與警告圖示。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-133">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
     <span data-ttu-id="d4aa0-134">執行 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 或更早版本的散發者無法使用這個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-134">This tab is not available for Distributors that are running versions of [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or earlier.</span></span>  
  
-   <span data-ttu-id="d4aa0-135">**[代理程式]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-135">**Agents** tab</span></span>  
  
     <span data-ttu-id="d4aa0-136">此索引標籤會顯示有關所有複寫類型使用之代理程式和工作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-136">This tab displays detailed information about the agents and jobs that are used by all types of replication.</span></span> <span data-ttu-id="d4aa0-137">這個索引標籤可讓您啟動和停止每個代理程式和工作。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-137">The tab also let you start and stop each agent and job.</span></span>  
  
 <span data-ttu-id="d4aa0-138">「複寫監視器」也提供散發者節點的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-138">Replication Monitor also provides a context menu for the Distributor node.</span></span> <span data-ttu-id="d4aa0-139">以滑鼠右鍵按一下左窗格中的散發者可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-139">Right-click a Distributor in the left pane to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="d4aa0-140">將發行者加入至複寫監視器。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-140">Add a Publisher to Replication Monitor.</span></span>  
  
-   <span data-ttu-id="d4aa0-141">編輯散發者的複寫監視器設定。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-141">Edit Replication Monitor settings for the Distributor.</span></span>  
  
-   <span data-ttu-id="d4aa0-142">切換至 [發行者群組] 檢視。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-142">Switch to the Publisher Group view.</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-publishers"></a><span data-ttu-id="d4aa0-143">檢視與發行者相關的資訊並執行工作</span><span class="sxs-lookup"><span data-stu-id="d4aa0-143">Viewing Information and Performing Tasks Related to Publishers</span></span>  
 <span data-ttu-id="d4aa0-144">「複寫監視器」會在下列三個索引標籤上顯示發行者的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-144">Replication Monitor displays information about Publishers on three tabs:</span></span>  
  
-   <span data-ttu-id="d4aa0-145">**[發行集]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-145">**Publications** tab</span></span>  
  
     <span data-ttu-id="d4aa0-146">此索引標籤提供在發行者端的所有發行集之摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-146">This tab provides summary information for all publications at a Publisher.</span></span>  
  
-   <span data-ttu-id="d4aa0-147">**[訂閱監看清單]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-147">**Subscription Watch List** tab</span></span>  
  
     <span data-ttu-id="d4aa0-148">此索引標籤用於顯示在所選發行者端的所有可用發行集之訂閱相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-148">This tab is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="d4aa0-149">您可以篩選訂閱清單以查看錯誤、警告以及任何執行不良的訂閱。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-149">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="d4aa0-150">此索引標籤也可讓您存取訂閱屬性、存取與訂閱相關聯的一或多個代理程式之詳細資訊、重新初始化訂閱，以及驗證訂閱。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-150">The tab also allows you to: access subscription properties; access detailed information about the agent or agents associated with a subscription; reinitialize subscriptions; and validate subscriptions.</span></span>  
  
     <span data-ttu-id="d4aa0-151">**[訂閱監看清單]** 索引標籤可協助回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-151">The **Subscription Watch List** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="d4aa0-152">哪些訂閱的速度慢？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-152">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="d4aa0-153">設定這個索引標籤上的選項，使方格依相關效能的順序顯示訂閱。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-153">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="d4aa0-154">我的複寫系統狀況是否良好？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-154">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="d4aa0-155">這個索引標籤上的方格會顯示需要您注意之任何訂閱的錯誤與警告圖示。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-155">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
     <span data-ttu-id="d4aa0-156">如果散發者執行的是 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]之前的版本，則不會顯示此索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-156">This tab is not displayed for Distributors running versions prior to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="d4aa0-157">**[代理程式]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-157">**Agents** tab</span></span>  
  
     <span data-ttu-id="d4aa0-158">此索引標籤會顯示有關所有複寫類型使用之代理程式和工作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-158">This tab displays detailed information about the agents and jobs used by all types of replication.</span></span> <span data-ttu-id="d4aa0-159">您也可以用這個索引標籤來啟動和停止每個代理程式和工作。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-159">The tab also allows you to start and stop each agent and job.</span></span>  
  
 <span data-ttu-id="d4aa0-160">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-160">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="d4aa0-161">「複寫監視器」也提供發行者節點的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-161">Replication Monitor also provides a context menu for the Publisher node.</span></span> <span data-ttu-id="d4aa0-162">以滑鼠右鍵按一下左窗格中的發行者可以：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-162">Right-click a Publisher in the left pane to:</span></span>  
  
-   <span data-ttu-id="d4aa0-163">編輯發行者的複寫監視器設定</span><span class="sxs-lookup"><span data-stu-id="d4aa0-163">Edit Replication Monitor settings for the Publisher</span></span>  
  
-   <span data-ttu-id="d4aa0-164">從複寫監視器移除發行者</span><span class="sxs-lookup"><span data-stu-id="d4aa0-164">Remove the Publisher from Replication Monitor</span></span>  
  
-   <span data-ttu-id="d4aa0-165">檢視和編輯代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="d4aa0-165">View and edit agent profiles</span></span>  
  
-   <span data-ttu-id="d4aa0-166">連接到儲存發行者相關資訊的散發者或中斷與散發者的連接</span><span class="sxs-lookup"><span data-stu-id="d4aa0-166">Connect to or disconnect from the Distributor that stores information about the Publisher</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-publications"></a><span data-ttu-id="d4aa0-167">檢視與發行集相關的資訊並執行工作</span><span class="sxs-lookup"><span data-stu-id="d4aa0-167">Viewing Information and Performing Tasks Related to Publications</span></span>  
 <span data-ttu-id="d4aa0-168">「複寫監視器」會在三個索引標籤上及一些詳細資料視窗中，顯示發行集的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-168">Replication Monitor displays information about publications on three tabs and a number of detail windows:</span></span>  
  
-   <span data-ttu-id="d4aa0-169">**[所有訂閱]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-169">**All Subscriptions** tab</span></span>  
  
     <span data-ttu-id="d4aa0-170">這個索引標籤會顯示有關選取之發行集的所有訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-170">This tab displays information about all subscriptions to the selected publication.</span></span> <span data-ttu-id="d4aa0-171">依預設，此索引標籤會依優先順序排序：錯誤、警告，然後是以遞增順序排列的效能，任何效能不良的訂閱會位在頂端。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-171">By default, this tab is sorted in priority order: errors, then warnings, then in increasing order of performance, with any poorly performing subscriptions at the top.</span></span>  
  
     <span data-ttu-id="d4aa0-172">**[所有訂閱]** 索引標籤可協助回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-172">The **All Subscriptions** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="d4aa0-173">哪些訂閱的速度慢？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-173">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="d4aa0-174">設定這個索引標籤上的選項，使方格依相關效能的順序顯示訂閱。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-174">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="d4aa0-175">我的複寫系統狀況是否良好？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-175">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="d4aa0-176">這個索引標籤上的方格會顯示需要您注意之任何訂閱的錯誤與警告圖示。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-176">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
-   <span data-ttu-id="d4aa0-177">**[代理程式]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-177">**Agents** tab</span></span>  
  
     <span data-ttu-id="d4aa0-178">此索引標籤會顯示複寫所使用之代理程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-178">This tab displays information about the agents that are used by replication.</span></span> <span data-ttu-id="d4aa0-179">這個索引標籤會顯示下列代理程式的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-179">This tab displays information about the following agents:</span></span>  
  
    -   <span data-ttu-id="d4aa0-180">所有發行集所使用的快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-180">The Snapshot Agent, which is used by all publications.</span></span>  
  
    -   <span data-ttu-id="d4aa0-181">所有交易式發行集所使用的記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-181">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
    -   <span data-ttu-id="d4aa0-182">針對佇列更新訂閱啟用之交易式發行集所使用的佇列讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-182">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
     <span data-ttu-id="d4aa0-183">索引標籤也可以讓您執行下列工作：存取每個代理程式的詳細資訊，以及啟動和停止每個代理程式。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-183">The tab also allows for you to perform the following tasks: access detailed information about each agent, and start and stop each agent.</span></span> <span data-ttu-id="d4aa0-184">如需與訂閱相關聯的代理程式相關資訊 (「散發代理程式」和「合併代理程式」)，請參閱本主題中的「檢視與訂閱相關的資訊並執行工作」一節。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-184">For information about agents that are associated with subscriptions (the Distribution Agent and Merge Agent), see the section "Viewing Information and Performing Tasks Related to Subscriptions" in this topic.</span></span>  
  
-   <span data-ttu-id="d4aa0-185">**[警告]** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d4aa0-185">**Warnings** tab</span></span>  
  
     <span data-ttu-id="d4aa0-186">這個索引標籤可用來為代理程式指定警告和警示。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-186">This tab enables you to specify warnings and alerts for agents.</span></span> <span data-ttu-id="d4aa0-187">如需相關資訊，請參閱 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-187">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="d4aa0-188">**[追蹤 Token]** 索引標籤 (僅適用於異動複寫)</span><span class="sxs-lookup"><span data-stu-id="d4aa0-188">**Tracer Tokens** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="d4aa0-189">這個索引標籤能讓您測量延遲，在發行者端所認可之交易與在訂閱者端所認可之對應交易之間經過的時間。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-189">This tab allows you to measure latency, the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span>  
  
     <span data-ttu-id="d4aa0-190">此索引標籤可協助回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-190">This tab helps answers the following question:</span></span>  
  
    -   <span data-ttu-id="d4aa0-191">目前一個認可的交易要到達異動複寫中的訂閱者需花多久的時間？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-191">How long will it take a transaction committed now to reach a Subscriber in transactional replication?</span></span>  
  
         <span data-ttu-id="d4aa0-192">檢視交易透過系統傳輸的總時間，並與先前的時間比較。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-192">View the total time for a transaction to travel through the system and also compare it to previous times.</span></span>  
  
     <span data-ttu-id="d4aa0-193">如果散發者執行的是 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 或更早版本，則不會顯示此索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-193">This tab is not displayed for Distributors running [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or earlier.</span></span> <span data-ttu-id="d4aa0-194">如需追蹤 Token 的詳細資訊，請參閱[針對異動複寫測量延遲及驗證連線](measure-latency-and-validate-connections-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-194">For more information on tracer tokens, see [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="d4aa0-195">與發行集相關聯的代理程式之詳細資料視窗。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-195">Detail windows for the agents associated with a publication.</span></span> <span data-ttu-id="d4aa0-196">下列代理程式與發行集相關聯：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-196">The following agents are associated with publications:</span></span>  
  
    -   <span data-ttu-id="d4aa0-197">所有發行集所使用的快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-197">The Snapshot Agent, which is used by all publications.</span></span>  
  
    -   <span data-ttu-id="d4aa0-198">所有交易式發行集所使用的記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-198">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
    -   <span data-ttu-id="d4aa0-199">針對佇列更新訂閱啟用之交易式發行集所使用的佇列讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-199">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
     <span data-ttu-id="d4aa0-200">按兩下「複寫監視器」中的代理程式，可存取詳細資料視窗中的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-200">Double-click an agent in Replication Monitor to access information in a detail window.</span></span> <span data-ttu-id="d4aa0-201">除了上述所列的代理程式外，還有與訂閱相關聯的代理程式：快照式和交易式發行集的訂閱之「散發代理程式」，以及合併發行集的訂閱之「合併代理程式」。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-201">In addition to the agents listed above, there are agents associated with subscriptions: the Distribution Agent for subscriptions to snapshot and transactional publications; and the Merge Agent for subscriptions to merge publications.</span></span> <span data-ttu-id="d4aa0-202">如需詳細資訊，請參閱本主題中的「檢視與訂閱相關的資訊並執行工作」一節。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-202">For more information, see the section "Viewing Information and Performing Tasks Related to Subscriptions" in this topic.</span></span>  
  
     <span data-ttu-id="d4aa0-203">代理程式詳細資料視窗提供代理程式工作階段的相關資訊，包括開始時間、結束時間、持續時間，以及在工作階段內執行的動作。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-203">The agent detail windows provide information about agent sessions, including start time, end time, duration, and the actions performed in a session.</span></span> <span data-ttu-id="d4aa0-204">這些資訊可協助回答下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-204">They help to answer the following question:</span></span>  
  
    -   <span data-ttu-id="d4aa0-205">代理程式為何沒有執行？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-205">Why is an agent not running?</span></span>  
  
         <span data-ttu-id="d4aa0-206">可用的錯誤訊息提供代理程式為何不在執行中的詳細資訊，並提供與發行集相關聯的代理程式問題之疑難排解起點。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-206">The error messages available provide detailed information on why an agent is not running and provide a starting point for troubleshooting issues with the agents associated with a publication.</span></span>  
  
 <span data-ttu-id="d4aa0-207">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-207">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="d4aa0-208">「複寫監視器」也提供發行集節點的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-208">Replication Monitor also provides a context menu for the publications node.</span></span> <span data-ttu-id="d4aa0-209">以滑鼠右鍵按一下左窗格中的發行集可以：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-209">Right-click a publication in the left pane to:</span></span>  
  
-   <span data-ttu-id="d4aa0-210">重新初始化發行集的所有訂閱</span><span class="sxs-lookup"><span data-stu-id="d4aa0-210">Reinitialize all subscriptions to a publication</span></span>  
  
-   <span data-ttu-id="d4aa0-211">驗證發行集的所有訂閱</span><span class="sxs-lookup"><span data-stu-id="d4aa0-211">Validate all subscriptions to a publication</span></span>  
  
-   <span data-ttu-id="d4aa0-212">產生發行集的快照集</span><span class="sxs-lookup"><span data-stu-id="d4aa0-212">Generate a snapshot for a publication</span></span>  
  
-   <span data-ttu-id="d4aa0-213">檢視和編輯發行集屬性</span><span class="sxs-lookup"><span data-stu-id="d4aa0-213">View and edit publication properties</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-subscriptions"></a><span data-ttu-id="d4aa0-214">檢視與訂閱相關的資訊並執行工作</span><span class="sxs-lookup"><span data-stu-id="d4aa0-214">Viewing Information and Performing Tasks Related to Subscriptions</span></span>  
 <span data-ttu-id="d4aa0-215">「複寫監視器」會在一些不同的索引標籤上顯示與訂閱相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-215">Replication Monitor displays information about subscriptions on a number of different tabs.</span></span> <span data-ttu-id="d4aa0-216">按兩下「複寫監視器」中的訂閱，可在詳細資料視窗中存取這些索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-216">Double-click a subscription in Replication Monitor to access these tabs in a detail window.</span></span> <span data-ttu-id="d4aa0-217">所有索引標籤都可協助回答「代理程式為何不在執行中？」的問題。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-217">All of the tabs are useful in answering the question "Why is an agent not running?"</span></span> <span data-ttu-id="d4aa0-218">可用的錯誤訊息提供代理程式為何不在執行中的詳細資訊，並提供與訂閱相關聯的代理程式問題之疑難排解起點。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-218">The error messages available provide detailed information on why an agent is not running and provide a starting point for troubleshooting issues with the agents associated with a subscription.</span></span>  
  
-   <span data-ttu-id="d4aa0-219">**[所有訂閱]** 及 **[訂閱監看清單]**</span><span class="sxs-lookup"><span data-stu-id="d4aa0-219">**All Subscriptions tab** and **Subscription Watch List tab.**</span></span>  
  
     <span data-ttu-id="d4aa0-220">這些索引標籤在本主題前文中說明。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-220">These tabs are described earlier in this topic.</span></span>  
  
-   <span data-ttu-id="d4aa0-221">**[發行者到散發者記錄]** 索引標籤 (僅適用於異動複寫)</span><span class="sxs-lookup"><span data-stu-id="d4aa0-221">**Publisher to Distributor History** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="d4aa0-222">此索引標籤會顯示關於發行集的「記錄讀取器代理程式」之資訊 (此索引標籤與「記錄讀取器代理程式」詳細資料視窗相同)。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-222">This tab displays information on the Log Reader Agent for a publication (the tab is identical to the Log Reader Agent details window).</span></span>  
  
-   <span data-ttu-id="d4aa0-223">**[散發者到訂閱者記錄]** 索引標籤 (快照式複寫和異動複寫)</span><span class="sxs-lookup"><span data-stu-id="d4aa0-223">**Distributor to Subscriber History** tab (snapshot replication and transactional replication)</span></span>  
  
     <span data-ttu-id="d4aa0-224">此索引標籤會顯示關於訂閱的「散發代理程式」之資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-224">This tab displays information on the Distribution Agent for a subscription.</span></span>  
  
-   <span data-ttu-id="d4aa0-225">**[未散發的命令]** 索引標籤 (僅適用於異動複寫)</span><span class="sxs-lookup"><span data-stu-id="d4aa0-225">**Undistributed Commands** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="d4aa0-226">此索引標籤會顯示散發資料庫中尚未傳送到所選訂閱者的命令數目，以及傳送這些命令的預估時間等相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-226">This tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands.</span></span> <span data-ttu-id="d4aa0-227">此索引標籤可協助回答「我的訂閱落後多少？」的問題。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-227">The tab helps answer the question, "How far behind is my subscription?"</span></span> <span data-ttu-id="d4aa0-228">如果散發者執行的是 SQL Server 2005 之前的版本，則不會顯示此索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-228">This tab is not displayed for Distributors running versions prior to SQL Server 2005.</span></span>  
  
-   <span data-ttu-id="d4aa0-229">**[同步處理記錄]** 索引標籤 (僅適用於合併式複寫)</span><span class="sxs-lookup"><span data-stu-id="d4aa0-229">**Synchronization History** tab (merge replication only)</span></span>  
  
     <span data-ttu-id="d4aa0-230">此索引標籤會顯示關於訂閱的「合併代理程式」之資訊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-230">This tab displays information on the Merge Agent for a subscription.</span></span> <span data-ttu-id="d4aa0-231">此索引標籤可協助回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-231">This tab helps answer the following question:</span></span>  
  
    -   <span data-ttu-id="d4aa0-232">為何我的合併訂閱速度很慢？</span><span class="sxs-lookup"><span data-stu-id="d4aa0-232">Why is my merge subscription slow?</span></span>  
  
         <span data-ttu-id="d4aa0-233">此索引標籤提供在同步處理期間處理的每個發行項之詳細統計資料，包括在每個處理階段 (上傳變更、下載變更等等) 內花費的時間量。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-233">This tab provides detailed statistics for each article processed during synchronization, including the amount of time spent in each processing phase (uploading changes, downloading changes, and so on).</span></span> <span data-ttu-id="d4aa0-234">這可協助找出導致速度變慢的特定資料表，且最適合在此進行合併訂閱效能問題的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-234">It can help pinpoint specific tables that are causing slowdowns and is the best place to troubleshoot performance issues with merge subscriptions.</span></span>  
  
 <span data-ttu-id="d4aa0-235">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-235">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>
  
## <a name="viewing-information-and-performing-tasks-related-to-agent-profiles"></a><span data-ttu-id="d4aa0-236">檢視與代理程式設定檔相關的資訊並執行工作</span><span class="sxs-lookup"><span data-stu-id="d4aa0-236">Viewing Information and Performing Tasks Related to Agent Profiles</span></span>  
 <span data-ttu-id="d4aa0-237">「複寫監視器」包含一些管理代理程式設定檔的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-237">Replication Monitor includes a number of dialog boxes for managing agent profiles.</span></span> <span data-ttu-id="d4aa0-238">代理程式設定檔是代理程式的參數集合，用於決定代理程式行為。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-238">Agent profiles are sets of parameters for an agent that determine agent behavior.</span></span> <span data-ttu-id="d4aa0-239">如需相關資訊，請參閱 [Replication Agent Profiles](../agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-239">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span> <span data-ttu-id="d4aa0-240">對話方塊包括：</span><span class="sxs-lookup"><span data-stu-id="d4aa0-240">The dialog boxes are:</span></span>  
  
-   <span data-ttu-id="d4aa0-241">**代理程式設定檔**</span><span class="sxs-lookup"><span data-stu-id="d4aa0-241">**Agent Profiles**</span></span>  
  
     <span data-ttu-id="d4aa0-242">此對話方塊可讓您變更設定檔的屬性、建立及刪除設定檔、指定預設設定檔，以及指定所有特定類型的代理程式 (如快照集代理程式) 都應該使用給定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-242">This dialog box allows you to: change the properties of profiles; create and delete profiles; specify a default profile; and specify that all agents of a specific type (such as Snapshot Agents) should use a given profile.</span></span>  
  
-   <span data-ttu-id="d4aa0-243">**\<AgentProfileName>屬性**</span><span class="sxs-lookup"><span data-stu-id="d4aa0-243">**\<AgentProfileName> Properties**</span></span>  
  
     <span data-ttu-id="d4aa0-244">此對話方塊可讓您檢視和編輯設定檔中的參數設定。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-244">This dialog box allows you to view and edit the parameter settings in a profile.</span></span>  
  
-   <span data-ttu-id="d4aa0-245">**新增代理程式設定檔**</span><span class="sxs-lookup"><span data-stu-id="d4aa0-245">**New Agent Profile**</span></span>  
  
     <span data-ttu-id="d4aa0-246">此對話方塊可讓您建立新設定檔，並選擇性地包含現有設定檔中的值。</span><span class="sxs-lookup"><span data-stu-id="d4aa0-246">This dialog box allows you to create a new profile, optionally including the values from an existing profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4aa0-247">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4aa0-247">See Also</span></span>  
 [<span data-ttu-id="d4aa0-248">監視複寫</span><span class="sxs-lookup"><span data-stu-id="d4aa0-248">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
