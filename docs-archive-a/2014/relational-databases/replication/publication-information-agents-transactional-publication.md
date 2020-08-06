---
title: 發行集資訊，代理程式 (交易式發行集) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1a3d50da15ea653a7911e65ad888d5997f47a3f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585288"
---
# <a name="publication-information-agents-transactional-publication"></a><span data-ttu-id="23e04-102">發行集資訊，代理程式 (交易式發行集)</span><span class="sxs-lookup"><span data-stu-id="23e04-102">Publication Information, Agents (Transactional Publication)</span></span>
  <span data-ttu-id="23e04-103">**[代理程式]** 索引標籤會顯示所選取發行集之代理程式的摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="23e04-103">The **Agents** tab displays summary information on the agents for the selected publication.</span></span> <span data-ttu-id="23e04-104">所有的交易式發行集，都會顯示快照集代理程式與記錄讀取器代理程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="23e04-104">Information on the Snapshot Agent and Log Reader Agent is displayed for all transactional publications.</span></span> <span data-ttu-id="23e04-105">已啟用佇列更新訂閱的交易式發行集，才會顯示佇列讀取器代理程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="23e04-105">Information on the Queue Reader Agent is displayed for those transactional publications that are enabled for queued updating subscriptions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="23e04-106">選項</span><span class="sxs-lookup"><span data-stu-id="23e04-106">Options</span></span>  
 <span data-ttu-id="23e04-107">如需代理程式的詳細資訊及其相關的工作，請以滑鼠右鍵按一下該代理程式的資料列，然後按一下捷徑功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="23e04-107">For more detailed information and tasks related to an agent, right-click the row for that agent, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="23e04-108">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="23e04-108">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="23e04-109">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="23e04-109">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="23e04-110">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="23e04-110">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="23e04-111">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="23e04-111">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="23e04-112">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="23e04-112">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="23e04-113">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="23e04-113">Filter settings are specific to each grid.</span></span> <span data-ttu-id="23e04-114">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="23e04-114">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="23e04-115">**狀態**</span><span class="sxs-lookup"><span data-stu-id="23e04-115">**Status**</span></span>  
 <span data-ttu-id="23e04-116">與發行集相關聯之每個複寫代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="23e04-116">The status of each replication agent associated with the publication.</span></span> <span data-ttu-id="23e04-117">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="23e04-117">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="23e04-118">錯誤</span><span class="sxs-lookup"><span data-stu-id="23e04-118">Error</span></span>  
  
-   <span data-ttu-id="23e04-119">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="23e04-119">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="23e04-120">未執行</span><span class="sxs-lookup"><span data-stu-id="23e04-120">Not running</span></span>  
  
-   <span data-ttu-id="23e04-121">執行中</span><span class="sxs-lookup"><span data-stu-id="23e04-121">Running</span></span>  
  
-   <span data-ttu-id="23e04-122">Completed</span><span class="sxs-lookup"><span data-stu-id="23e04-122">Completed</span></span>  
  
 <span data-ttu-id="23e04-123">**代理程式**</span><span class="sxs-lookup"><span data-stu-id="23e04-123">**Agent**</span></span>  
 <span data-ttu-id="23e04-124">與發行集相關聯之每個複寫代理程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="23e04-124">The name of each replication agent associated with the publication.</span></span> <span data-ttu-id="23e04-125">散發代理程式與這個發行集的訂閱相關聯。</span><span class="sxs-lookup"><span data-stu-id="23e04-125">The Distribution Agent is associated with subscriptions to this publication.</span></span> <span data-ttu-id="23e04-126">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="23e04-126">For more information, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="23e04-127">**上次啟動時間**</span><span class="sxs-lookup"><span data-stu-id="23e04-127">**Last Start Time**</span></span>  
 <span data-ttu-id="23e04-128">代理程式上次啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="23e04-128">The last time the agent started.</span></span>  
  
 <span data-ttu-id="23e04-129">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="23e04-129">**Duration**</span></span>  
 <span data-ttu-id="23e04-130">代理程式已執行的時間量。</span><span class="sxs-lookup"><span data-stu-id="23e04-130">The amount of time the agent has run.</span></span> <span data-ttu-id="23e04-131">如果代理程式目前正在執行，此時間代表經過時間；如果代理程式是先前有執行過，則此時間代表總共時間。</span><span class="sxs-lookup"><span data-stu-id="23e04-131">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="23e04-132">**最後一個動作**</span><span class="sxs-lookup"><span data-stu-id="23e04-132">**Last Action**</span></span>  
 <span data-ttu-id="23e04-133">最近一次代理程式執行期間執行的最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="23e04-133">The last action performed during the most recent run of the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e04-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23e04-134">See Also</span></span>  
 <span data-ttu-id="23e04-135">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="23e04-135">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="23e04-136">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="23e04-136">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="23e04-137">監視複寫</span><span class="sxs-lookup"><span data-stu-id="23e04-137">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
