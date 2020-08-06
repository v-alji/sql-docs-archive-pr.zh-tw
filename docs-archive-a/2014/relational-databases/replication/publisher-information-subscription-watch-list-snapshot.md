---
title: 發行者資訊、訂閱監看清單 (快照式發行集、SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ea44958c81465570c036ab7dd83247fb55652f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701050"
---
# <a name="publisher-information-subscription-watch-list-snapshot-publication-sql-server-2005-and-later"></a><span data-ttu-id="5c064-102">發行者資訊，訂閱監看清單 (快照式發行集，SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="5c064-102">Publisher Information, Subscription Watch List (Snapshot Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="5c064-103">執行 **和更新版本的散發者可以使用** [訂閱監看清單] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 索引標籤。這個索引標籤的用途是顯示選取發行者端之所有可用發行集的相關訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="5c064-103">The **Subscription Watch List** tab is available for Distributors running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="5c064-104">您可以篩選訂閱清單以查看錯誤、警告以及任何執行不良的訂閱。</span><span class="sxs-lookup"><span data-stu-id="5c064-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="5c064-105">此索引標籤為管理員提供監視發行者端所有複寫活動的單一位置：複寫監視器會根據選取的複寫類型和 **[顯示]** 下拉式清單方塊中選擇的選項，顯示需要注意的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="5c064-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="5c064-106">由於此索引標籤上顯示的項目會依據目前的狀態與效能，因此唯有在目前符合 **[顯示]** 清單方塊中之選項的訂閱，才會在這個頁面上顯示。</span><span class="sxs-lookup"><span data-stu-id="5c064-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5c064-107">選項</span><span class="sxs-lookup"><span data-stu-id="5c064-107">Options</span></span>  
 <span data-ttu-id="5c064-108">如需詳細資訊以及與訂閱相關的工作，請以滑鼠右鍵按一下該訂閱的資料列，然後按一下捷徑功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="5c064-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="5c064-109">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="5c064-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="5c064-110">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="5c064-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="5c064-111">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="5c064-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="5c064-112">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="5c064-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="5c064-113">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="5c064-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="5c064-114">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="5c064-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="5c064-115">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="5c064-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="5c064-116">**顯示快照式訂閱**</span><span class="sxs-lookup"><span data-stu-id="5c064-116">**Show Snapshot Subscriptions**</span></span>  
 <span data-ttu-id="5c064-117">針對選取之發行者，選取要顯示的訂閱類型 (交易式、快照式或合併式)。</span><span class="sxs-lookup"><span data-stu-id="5c064-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="5c064-118">**顯示**</span><span class="sxs-lookup"><span data-stu-id="5c064-118">**Show**</span></span>  
 <span data-ttu-id="5c064-119">針對選取之訂閱類型，選取要顯示的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="5c064-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="5c064-120">例如，您可以選取只顯示有錯誤的訂閱。</span><span class="sxs-lookup"><span data-stu-id="5c064-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="5c064-121">**狀態**</span><span class="sxs-lookup"><span data-stu-id="5c064-121">**Status**</span></span>  
 <span data-ttu-id="5c064-122">每個訂閱的狀態，這是由快照集代理程式或散發代理程式的狀態所決定 (會顯示優先權較高的狀態)。</span><span class="sxs-lookup"><span data-stu-id="5c064-122">The status of each subscription, which is determined by the status of the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="5c064-123">依預設，包含訂閱資訊的方格會依 **[狀態]** 資料行排序。</span><span class="sxs-lookup"><span data-stu-id="5c064-123">By default, the grid containing subscription information is sorted by the **Status** column.</span></span> <span data-ttu-id="5c064-124">下列清單顯示可能的狀態值和值的排序順序 (例如，錯誤一律顯示在方格頂端)。</span><span class="sxs-lookup"><span data-stu-id="5c064-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="5c064-125">錯誤</span><span class="sxs-lookup"><span data-stu-id="5c064-125">Error</span></span>  
  
-   <span data-ttu-id="5c064-126">「即將過期/已過期」</span><span class="sxs-lookup"><span data-stu-id="5c064-126">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="5c064-127">未初始化的訂閱</span><span class="sxs-lookup"><span data-stu-id="5c064-127">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="5c064-128">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="5c064-128">Retrying failed command</span></span>  
  
-   <span data-ttu-id="5c064-129">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="5c064-129">Synchronizing</span></span>  
  
-   <span data-ttu-id="5c064-130">未進行同步處理</span><span class="sxs-lookup"><span data-stu-id="5c064-130">Not synchronizing</span></span>  
  
 <span data-ttu-id="5c064-131">當給定訂閱有一個以上的狀態時，排序順序也會決定要顯示哪一個值。</span><span class="sxs-lookup"><span data-stu-id="5c064-131">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="5c064-132">例如，若訂閱有錯誤而且即將過期，則 **[狀態]** 資料行會顯示 **[錯誤]**。</span><span class="sxs-lookup"><span data-stu-id="5c064-132">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="5c064-133">**[即將過期/已過期]** 和 **[未初始化的訂閱]** 狀態值均為警告。</span><span class="sxs-lookup"><span data-stu-id="5c064-133">The status values **Expiring soon/Expired** and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="5c064-134">顯示警告時，如果代理程式正在執行，則 **[狀態]** 資料行也會顯示。</span><span class="sxs-lookup"><span data-stu-id="5c064-134">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="5c064-135">例如，狀態可能是 **[執行中，即將過期/已過期]**。</span><span class="sxs-lookup"><span data-stu-id="5c064-135">For example, the status could be **Running, Expiring soon/Expired**.</span></span>  
  
 <span data-ttu-id="5c064-136">唯有設定了臨界值時，才會顯示 **[即將過期/已過期]** 狀態值。</span><span class="sxs-lookup"><span data-stu-id="5c064-136">The status value **Expiring soon/Expired** is displayed only if a threshold is set.</span></span> <span data-ttu-id="5c064-137">如需設定閾值的資訊，請參閱[在複寫監視器中設定閾值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="5c064-137">For information on setting thresholds, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="5c064-138">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="5c064-138">**Subscription**</span></span>  
 <span data-ttu-id="5c064-139">每一個訂閱的名稱，格式為： *SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="5c064-139">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="5c064-140">**發行**</span><span class="sxs-lookup"><span data-stu-id="5c064-140">**Publication**</span></span>  
 <span data-ttu-id="5c064-141">與訂閱同步處理的發行集名稱，格式如下： *PublicationDatabaseName: PublicationName*。</span><span class="sxs-lookup"><span data-stu-id="5c064-141">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="5c064-142">**上次同步處理日期**</span><span class="sxs-lookup"><span data-stu-id="5c064-142">**Last Synchronization**</span></span>  
 <span data-ttu-id="5c064-143">散發代理程式上次執行的時間。</span><span class="sxs-lookup"><span data-stu-id="5c064-143">The time at which the Distribution Agent last ran.</span></span> <span data-ttu-id="5c064-144">如果正在進行同步處理，就會顯示 **[進行中]** 。</span><span class="sxs-lookup"><span data-stu-id="5c064-144">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c064-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c064-145">See Also</span></span>  
 <span data-ttu-id="5c064-146">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="5c064-146">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="5c064-147">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="5c064-147">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="5c064-148">監視複寫</span><span class="sxs-lookup"><span data-stu-id="5c064-148">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
