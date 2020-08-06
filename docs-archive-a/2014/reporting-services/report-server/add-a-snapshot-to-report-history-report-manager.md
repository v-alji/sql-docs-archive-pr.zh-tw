---
title: 將快照集新增至報表記錄 (報表管理員) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
helpviewer_keywords:
- report history [Reporting Services], adding snapshots
- historical data [Reporting Services]
- snapshots [Reporting Services], adding report snapshots
- adding snapshots to report history
- report snapshots [Reporting Services], adding
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 84d4c264ab0b82fca2a34e6356b53113d63e6994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597628"
---
# <a name="add-a-snapshot-to-report-history-report-manager"></a><span data-ttu-id="b81dc-102">將快照集加入報表記錄 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="b81dc-102">Add a Snapshot to Report History (Report Manager)</span></span>

<span data-ttu-id="b81dc-103">報表記錄是您在經過一段時間後建立之報表快照集的集合。</span><span class="sxs-lookup"><span data-stu-id="b81dc-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="b81dc-104">報表快照集是一種報表，它包含在特定時間點擷取的配置資訊和查詢結果。</span><span class="sxs-lookup"><span data-stu-id="b81dc-104">A report snapshot is a report that contains layout information and query results that were retrieved at a specific point in time.</span></span> <span data-ttu-id="b81dc-105">報表快照集和視需要報表不同，視需要報表會在您選取報表時取得最新的查詢結果，而報表快照集是依排程處理，並儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="b81dc-105">Unlike on-demand reports, which get up-to-date query results when you select the report, report snapshots are processed on a schedule and then saved to a report server.</span></span> <span data-ttu-id="b81dc-106">您選取報表快照集以供檢視時，報表伺服器會從報表伺服器資料庫擷取儲存的報表，並顯示建立快照集當時的資料與配置。</span><span class="sxs-lookup"><span data-stu-id="b81dc-106">When you select a report snapshot for viewing, the report server retrieves the stored report from the report server database and shows the data and layout that were current for the report at the time the snapshot was created.</span></span>  
  
<span data-ttu-id="b81dc-107">報表快照集不會以特定轉譯格式儲存。</span><span class="sxs-lookup"><span data-stu-id="b81dc-107">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="b81dc-108">而是只有在使用者或應用程式要求它時，報表快照集才以最後的檢視格式轉譯 (例如 HTML)。</span><span class="sxs-lookup"><span data-stu-id="b81dc-108">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="b81dc-109">延遲轉譯讓快照集具有可攜性。</span><span class="sxs-lookup"><span data-stu-id="b81dc-109">Deferred rendering makes a snapshot portable.</span></span> <span data-ttu-id="b81dc-110">報表可以使用要求的裝置或 Web 瀏覽器的正確格式轉譯。</span><span class="sxs-lookup"><span data-stu-id="b81dc-110">The report can be rendered in the correct format for the requesting device or Web browser.</span></span>  
  
## <a name="to-manually-add-snapshots-to-report-history"></a><span data-ttu-id="b81dc-111">若要手動將快照集加入至報表記錄</span><span class="sxs-lookup"><span data-stu-id="b81dc-111">To manually add snapshots to report history</span></span>

1. <span data-ttu-id="b81dc-112">在報表管理員中，巡覽至 [內容]  頁面，將滑鼠游標停留在您想要檢視記錄的項目上方，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="b81dc-112">In Report Manager, navigate to the **Contents** page, and hover over the item that you want to view history for, and click the drop-down arrow.</span></span>
  
2. <span data-ttu-id="b81dc-113">在下拉式功能表中，按一下 **[檢視報表記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="b81dc-113">In the drop-down menu, click **View Report History**.</span></span>  
  
3. <span data-ttu-id="b81dc-114">按一下 **[新增快照集]** 。</span><span class="sxs-lookup"><span data-stu-id="b81dc-114">Click **New Snapshot**.</span></span> <span data-ttu-id="b81dc-115">**[執行時]** 資料行裡會建立一個新的快照集。</span><span class="sxs-lookup"><span data-stu-id="b81dc-115">A new snapshot is created in the **When Run** column.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b81dc-116">管理員必須將報表記錄設定為 **[允許手動建立記錄]**，才能執行此作業。</span><span class="sxs-lookup"><span data-stu-id="b81dc-116">In order to do this, the report history must be configured by the administrator to **Allow history to be created manually**.</span></span> <span data-ttu-id="b81dc-117">如需詳細資訊，請參閱 [限制報表記錄 &#40;報表管理員&#41;](../reports/limit-report-history-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="b81dc-117">For more information, see [Limit Report History &#40;Report Manager&#41;](../reports/limit-report-history-report-manager.md).</span></span>

4. <span data-ttu-id="b81dc-118">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="b81dc-118">Click **Apply**.</span></span>

## <a name="to-automatically-add-all-snapshots-to-report-history"></a><span data-ttu-id="b81dc-119">若要自動將所有快照集加入報表記錄</span><span class="sxs-lookup"><span data-stu-id="b81dc-119">To automatically add all snapshots to report history</span></span>  
  
1. <span data-ttu-id="b81dc-120">若為已經設定成當做報表執行快照集執行的報表，您可以設定其他屬性，以便在每次重新整理快照集時，將快照集的副本儲存至報表記錄。</span><span class="sxs-lookup"><span data-stu-id="b81dc-120">For a report that is already configured to run as a report execution snapshot, you can set additional properties to save a copy of the snapshot to report history each time the snapshot is refreshed.</span></span>  
  
2. <span data-ttu-id="b81dc-121">在報表管理員中，巡覽至 [內容]  頁面，將滑鼠游標停留在您想要檢視記錄的項目上方，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="b81dc-121">In Report Manager, navigate to the **Contents** page, hover over the item that you want to view history for, and click the drop-down arrow.</span></span>  
  
3. <span data-ttu-id="b81dc-122">在下拉式功能表中，按一下 **[管理]** 。</span><span class="sxs-lookup"><span data-stu-id="b81dc-122">In the drop-down menu, click **Manage**.</span></span>  
  
4. <span data-ttu-id="b81dc-123">按一下 **[快照集選項]** 。</span><span class="sxs-lookup"><span data-stu-id="b81dc-123">Click **Snapshot Options**.</span></span>  
  
5. <span data-ttu-id="b81dc-124">選取 **[將所有報表執行快照集儲存在記錄中]** 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b81dc-124">Select the check box for **Store all report execution snapshots in history**.</span></span>  
  
6. <span data-ttu-id="b81dc-125">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="b81dc-125">Click **Apply**.</span></span>  
  
### <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a><span data-ttu-id="b81dc-126">若要依照排程自動將快照集加入報表記錄</span><span class="sxs-lookup"><span data-stu-id="b81dc-126">To automatically add snapshots to report history based on a schedule</span></span>  
  
1. <span data-ttu-id="b81dc-127">在報表管理員中，巡覽至 [內容]  頁面，將滑鼠游標停留在您想要檢視記錄的項目上方，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="b81dc-127">In Report Manager, navigate to the **Contents** page, and hover over the item that you want to view history for, and click the drop-down arrow.</span></span>  
  
2. <span data-ttu-id="b81dc-128">在下拉式功能表中，按一下 **[管理]** 。</span><span class="sxs-lookup"><span data-stu-id="b81dc-128">In the drop-down menu, click **Manage**.</span></span>  
  
3. <span data-ttu-id="b81dc-129">按一下 **[快照集選項]** 。</span><span class="sxs-lookup"><span data-stu-id="b81dc-129">Click **Snapshot Options**.</span></span>  
  
4. <span data-ttu-id="b81dc-130">選取 **[使用下列排程將快照集加入至報表記錄]** 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b81dc-130">Select the check box for **Use the following schedule to add snapshots to report history**.</span></span> <span data-ttu-id="b81dc-131">執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b81dc-131">Perform one of the following:</span></span>  
  
    - <span data-ttu-id="b81dc-132">選取 [報表特定排程]  。</span><span class="sxs-lookup"><span data-stu-id="b81dc-132">Select **Report-specific schedule**.</span></span> <span data-ttu-id="b81dc-133">填入排程詳細資料，選取排程的開始和結束日期，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b81dc-133">Fill in the schedule details, select the start and end dates for the schedule, and then click **OK**.</span></span>  
  
    - <span data-ttu-id="b81dc-134">選取 **[共用排程]** 。</span><span class="sxs-lookup"><span data-stu-id="b81dc-134">Select **Shared schedule**.</span></span> <span data-ttu-id="b81dc-135">從清單中，選取喜好的排程。</span><span class="sxs-lookup"><span data-stu-id="b81dc-135">From the list, select the preferred schedule.</span></span>  
  
5. <span data-ttu-id="b81dc-136">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="b81dc-136">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b81dc-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b81dc-137">See Also</span></span>

- [<span data-ttu-id="b81dc-138">設定報表的執行屬性 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="b81dc-138">Configure Execution Properties for a Report  &#40;Report Manager&#41;</span></span>](../reports/configure-execution-properties-for-a-report-report-manager.md)
- [<span data-ttu-id="b81dc-139">開啟及關閉報表 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="b81dc-139">Open and Close a Report &#40;Report Manager&#41;</span></span>](../reports/open-and-close-a-report-report-manager.md)
- [<span data-ttu-id="b81dc-140">限制報表記錄 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="b81dc-140">Limit Report History &#40;Report Manager&#41;</span></span>](../reports/limit-report-history-report-manager.md)
- [<span data-ttu-id="b81dc-141">排程</span><span class="sxs-lookup"><span data-stu-id="b81dc-141">Schedules</span></span>](../subscriptions/schedules.md)   
- [<span data-ttu-id="b81dc-142">報表管理員 &#40;SSRS 原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="b81dc-142">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)