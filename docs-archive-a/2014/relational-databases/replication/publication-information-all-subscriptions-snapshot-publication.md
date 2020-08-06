---
title: 發行集資訊，所有訂閱 (快照式發行集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75eb85adae46481ddd4360f095c00060af5677fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596656"
---
# <a name="publication-information-all-subscriptions-snapshot-publication"></a><span data-ttu-id="722c5-102">發行集資訊，所有訂閱 (快照式發行集)</span><span class="sxs-lookup"><span data-stu-id="722c5-102">Publication Information, All Subscriptions (Snapshot Publication)</span></span>
  <span data-ttu-id="722c5-103">**[所有訂閱]** 索引標籤，會顯示所選取快照式發行集之所有訂閱的資訊。</span><span class="sxs-lookup"><span data-stu-id="722c5-103">The **All Subscriptions** tab displays information on all subscriptions to the selected snapshot publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="722c5-104">選項</span><span class="sxs-lookup"><span data-stu-id="722c5-104">Options</span></span>  
 <span data-ttu-id="722c5-105">如需詳細資訊以及與訂閱相關的工作，請以滑鼠右鍵按一下該訂閱的資料列，然後按一下捷徑功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="722c5-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="722c5-106">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="722c5-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="722c5-107">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="722c5-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="722c5-108">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="722c5-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="722c5-109">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="722c5-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="722c5-110">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="722c5-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="722c5-111">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="722c5-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="722c5-112">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="722c5-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="722c5-113">**顯示**</span><span class="sxs-lookup"><span data-stu-id="722c5-113">**Show**</span></span>  
 <span data-ttu-id="722c5-114">僅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="722c5-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="722c5-115">針對選取之訂閱類型，選取要顯示的訂閱狀態。</span><span class="sxs-lookup"><span data-stu-id="722c5-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="722c5-116">例如，您可以選取只顯示有錯誤的訂閱。</span><span class="sxs-lookup"><span data-stu-id="722c5-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="722c5-117">**狀態**</span><span class="sxs-lookup"><span data-stu-id="722c5-117">**Status**</span></span>  
 <span data-ttu-id="722c5-118">每個訂閱的狀態，這是由快照集代理程式或散發代理程式的狀態所決定 (會顯示優先權較高的狀態)。</span><span class="sxs-lookup"><span data-stu-id="722c5-118">The status of each subscription, which is determined by the status of the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="722c5-119">依預設，包含訂閱資訊的方格會依 **[狀態]** 資料行排序。</span><span class="sxs-lookup"><span data-stu-id="722c5-119">By default, the grid containing subscription information is sorted by the **Status** column.</span></span> <span data-ttu-id="722c5-120">下列清單顯示可能的狀態值和值的排序順序 (例如，錯誤一律顯示在方格頂端)。</span><span class="sxs-lookup"><span data-stu-id="722c5-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="722c5-121">錯誤</span><span class="sxs-lookup"><span data-stu-id="722c5-121">Error</span></span>  
  
-   <span data-ttu-id="722c5-122">即將過期/已過期 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="722c5-122">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="722c5-123">未初始化的訂閱 (僅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="722c5-123">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="722c5-124">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="722c5-124">Retrying failed command</span></span>  
  
-   <span data-ttu-id="722c5-125">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="722c5-125">Synchronizing</span></span>  
  
-   <span data-ttu-id="722c5-126">未進行同步處理</span><span class="sxs-lookup"><span data-stu-id="722c5-126">Not synchronizing</span></span>  
  
 <span data-ttu-id="722c5-127">當給定訂閱有一個以上的狀態時，排序順序也會決定要顯示哪一個值。</span><span class="sxs-lookup"><span data-stu-id="722c5-127">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="722c5-128">例如，若訂閱有錯誤而且即將過期，則 **[狀態]** 資料行會顯示 **[錯誤]**。</span><span class="sxs-lookup"><span data-stu-id="722c5-128">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="722c5-129">**[即將過期/已過期]** 和 **[未初始化的訂閱]** 狀態值均為警告。</span><span class="sxs-lookup"><span data-stu-id="722c5-129">The status values **Expiring soon/Expired** and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="722c5-130">顯示警告時，如果代理程式正在執行，則 **[狀態]** 資料行也會顯示。</span><span class="sxs-lookup"><span data-stu-id="722c5-130">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="722c5-131">例如，狀態可能是 **[執行中，即將過期/已過期]**。</span><span class="sxs-lookup"><span data-stu-id="722c5-131">For example, the status could be **Running, Expiring soon/Expired**.</span></span>  
  
 <span data-ttu-id="722c5-132">唯有設定了臨界值時，才會顯示 **[即將過期/已過期]** 狀態值。</span><span class="sxs-lookup"><span data-stu-id="722c5-132">The status value **Expiring soon/Expired** is displayed only if a threshold is set.</span></span> <span data-ttu-id="722c5-133">如需設定閾值的資訊，請參閱[在複寫監視器中設定閾值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="722c5-133">For information on setting thresholds, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="722c5-134">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="722c5-134">**Subscription**</span></span>  
 <span data-ttu-id="722c5-135">每一個訂閱的名稱，格式為： *SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="722c5-135">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="722c5-136">**上次同步處理日期**</span><span class="sxs-lookup"><span data-stu-id="722c5-136">**Last Synchronization**</span></span>  
 <span data-ttu-id="722c5-137">散發代理程式上次執行的時間。</span><span class="sxs-lookup"><span data-stu-id="722c5-137">The time at which the Distribution Agent last ran.</span></span> <span data-ttu-id="722c5-138">如果正在進行同步處理，就會顯示 **[進行中]** 。</span><span class="sxs-lookup"><span data-stu-id="722c5-138">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="722c5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="722c5-139">See Also</span></span>  
 <span data-ttu-id="722c5-140">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="722c5-140">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="722c5-141">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="722c5-141">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="722c5-142">監視複寫</span><span class="sxs-lookup"><span data-stu-id="722c5-142">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
