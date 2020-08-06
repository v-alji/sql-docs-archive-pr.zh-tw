---
title: 發行集資訊，代理程式 (合併式發行集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.merge.f1
ms.assetid: 73ff590a-20da-4f10-b592-c60b7226d22b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8562a24066efd7cdad01f5559e97d8493a0f73a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585293"
---
# <a name="publication-information-agents-merge-publication"></a><span data-ttu-id="3f12c-102">發行集資訊，代理程式 (合併式發行集)</span><span class="sxs-lookup"><span data-stu-id="3f12c-102">Publication Information, Agents (Merge Publication)</span></span>
  <span data-ttu-id="3f12c-103">**[代理程式]** 索引標籤會顯示選取之發行集的快照集代理程式的摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="3f12c-103">The **Agents** tab displays summary information on the Snapshot Agent for the selected publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3f12c-104">選項。</span><span class="sxs-lookup"><span data-stu-id="3f12c-104">Options</span></span>  
 <span data-ttu-id="3f12c-105">如需快照集代理程式的詳細資訊與相關工作，請以滑鼠右鍵按一下代理程式的資料列，然後按一下快速鍵功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="3f12c-105">For more detailed information and tasks related to the Snapshot Agent, right-click the row for the agent, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="3f12c-106">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="3f12c-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="3f12c-107">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="3f12c-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="3f12c-108">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="3f12c-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="3f12c-109">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="3f12c-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="3f12c-110">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="3f12c-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="3f12c-111">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="3f12c-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="3f12c-112">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="3f12c-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="3f12c-113">**狀態**</span><span class="sxs-lookup"><span data-stu-id="3f12c-113">**Status**</span></span>  
 <span data-ttu-id="3f12c-114">快照集代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="3f12c-114">The status of the Snapshot Agent.</span></span> <span data-ttu-id="3f12c-115">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="3f12c-115">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="3f12c-116">錯誤</span><span class="sxs-lookup"><span data-stu-id="3f12c-116">Error</span></span>  
  
-   <span data-ttu-id="3f12c-117">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="3f12c-117">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="3f12c-118">未執行</span><span class="sxs-lookup"><span data-stu-id="3f12c-118">Not running</span></span>  
  
-   <span data-ttu-id="3f12c-119">Completed</span><span class="sxs-lookup"><span data-stu-id="3f12c-119">Completed</span></span>  
  
 <span data-ttu-id="3f12c-120">**代理程式**</span><span class="sxs-lookup"><span data-stu-id="3f12c-120">**Agent**</span></span>  
 <span data-ttu-id="3f12c-121">快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="3f12c-121">The Snapshot Agent.</span></span> <span data-ttu-id="3f12c-122">這是唯一與合併式發行集相關聯的代理程式。</span><span class="sxs-lookup"><span data-stu-id="3f12c-122">This is the only agent associated with a merge publication.</span></span> <span data-ttu-id="3f12c-123">合併代理程式與這個發行集的訂閱相關聯。</span><span class="sxs-lookup"><span data-stu-id="3f12c-123">The Merge Agent is associated with subscriptions to this publication.</span></span> <span data-ttu-id="3f12c-124">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3f12c-124">For more information, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="3f12c-125">**上次啟動時間**</span><span class="sxs-lookup"><span data-stu-id="3f12c-125">**Last Start Time**</span></span>  
 <span data-ttu-id="3f12c-126">代理程式上次啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="3f12c-126">The last time the agent started.</span></span>  
  
 <span data-ttu-id="3f12c-127">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="3f12c-127">**Duration**</span></span>  
 <span data-ttu-id="3f12c-128">代理程式已執行的時間量。</span><span class="sxs-lookup"><span data-stu-id="3f12c-128">The amount of time the agent has run.</span></span> <span data-ttu-id="3f12c-129">如果代理程式目前正在執行，此時間代表經過時間；如果代理程式是先前有執行過，則此時間代表總共時間。</span><span class="sxs-lookup"><span data-stu-id="3f12c-129">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="3f12c-130">**最後一個動作**</span><span class="sxs-lookup"><span data-stu-id="3f12c-130">**Last Action**</span></span>  
 <span data-ttu-id="3f12c-131">最近一次代理程式執行期間執行的最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="3f12c-131">The last action performed during the most recent run of the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f12c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f12c-132">See Also</span></span>  
 <span data-ttu-id="3f12c-133">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3f12c-133">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="3f12c-134">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3f12c-134">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="3f12c-135">監視複寫</span><span class="sxs-lookup"><span data-stu-id="3f12c-135">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
