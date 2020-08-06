---
title: 發行者資訊，代理程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.commonjobs.f1
ms.assetid: 2346c00d-c269-45a1-af14-68e7fd7ebd7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bdd2055ed022257524bc4d2784bdc333537be855
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585278"
---
# <a name="publisher-information-agents"></a><span data-ttu-id="f05a8-102">發行者資訊，代理程式</span><span class="sxs-lookup"><span data-stu-id="f05a8-102">Publisher Information, Agents</span></span>
  <span data-ttu-id="f05a8-103">**[代理程式]** 索引標籤會顯示與發行者相關聯之代理程式和維護作業的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="f05a8-103">The **Agents** tab displays information about the agents and maintenance jobs that are associated with the Publisher:</span></span>  
  
-   <span data-ttu-id="f05a8-104">快照集代理程式 (針對所有發行集顯示)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-104">Snapshot Agent, which is displayed for all publications.</span></span>  
  
-   <span data-ttu-id="f05a8-105">記錄讀取器代理程式 (針對所有交易式發行集顯示)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-105">Log Reader Agent, which is displayed for all transactional publications.</span></span>  
  
-   <span data-ttu-id="f05a8-106">佇列讀取器代理程式 (針對已啟用佇列更新訂閱的這些交易式發行集顯示)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-106">Queue Reader Agent, which is displayed for those transactional publications that are enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="f05a8-107">維護作業 (針對所有發行集顯示)：</span><span class="sxs-lookup"><span data-stu-id="f05a8-107">Maintenance jobs, displayed for all publications:</span></span>  
  
    -   <span data-ttu-id="f05a8-108">重新初始化資料驗證失敗的訂閱</span><span class="sxs-lookup"><span data-stu-id="f05a8-108">Reinitialize subscriptions that have data validation failures</span></span>  
  
    -   <span data-ttu-id="f05a8-109">代理程式記錄清除：散發</span><span class="sxs-lookup"><span data-stu-id="f05a8-109">Agent history cleanup: distribution</span></span>  
  
    -   <span data-ttu-id="f05a8-110">散發的複寫監視重新整理器</span><span class="sxs-lookup"><span data-stu-id="f05a8-110">Replication monitoring refresher for distribution</span></span>  
  
    -   <span data-ttu-id="f05a8-111">檢查複寫代理程式</span><span class="sxs-lookup"><span data-stu-id="f05a8-111">Replication agents checkup</span></span>  
  
    -   <span data-ttu-id="f05a8-112">清除散發：散發</span><span class="sxs-lookup"><span data-stu-id="f05a8-112">Distribution cleanup: distribution</span></span>  
  
    -   <span data-ttu-id="f05a8-113">到期的訂閱清除</span><span class="sxs-lookup"><span data-stu-id="f05a8-113">Expired subscription cleanup</span></span>  
  
 <span data-ttu-id="f05a8-114">如需這些作業的詳細資訊，請參閱[複寫代理程式管理](agents/replication-agent-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-114">For more information about these jobs, see [Replication Agent Administration](agents/replication-agent-administration.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f05a8-115">選項。</span><span class="sxs-lookup"><span data-stu-id="f05a8-115">Options</span></span>  
 <span data-ttu-id="f05a8-116">若要顯示某個代理程式或作業的相關資訊，請從 **[代理程式和作業類型]** 下拉式功能表中選取。</span><span class="sxs-lookup"><span data-stu-id="f05a8-116">To display information about an agent or job, select from the **Agent and Job Types** drop-down menu.</span></span> <span data-ttu-id="f05a8-117">如需更詳細的資訊以及與代理程式或作業相關的工作，請以滑鼠右鍵按一下該代理程式或作業的資料列，然後按一下快速鍵功能表上的選項。</span><span class="sxs-lookup"><span data-stu-id="f05a8-117">For more detailed information and tasks that are related to an agent or job, right-click the row for that agent or job, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="f05a8-118">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="f05a8-118">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="f05a8-119">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="f05a8-119">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="f05a8-120">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="f05a8-120">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="f05a8-121">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="f05a8-121">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="f05a8-122">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="f05a8-122">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="f05a8-123">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="f05a8-123">Filter settings are specific to each grid.</span></span> <span data-ttu-id="f05a8-124">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="f05a8-124">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="f05a8-125">下列各節將描述這個索引標籤上針對每個代理程式或作業顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="f05a8-125">The following sections describe the data that is displayed on this tab for each agent or job.</span></span>  
  
### <a name="snapshot-agent"></a><span data-ttu-id="f05a8-126">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="f05a8-126">Snapshot Agent</span></span>  
 <span data-ttu-id="f05a8-127">**狀態**</span><span class="sxs-lookup"><span data-stu-id="f05a8-127">**Status**</span></span>  
 <span data-ttu-id="f05a8-128">代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="f05a8-128">The status of the agent.</span></span> <span data-ttu-id="f05a8-129">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="f05a8-129">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="f05a8-130">錯誤</span><span class="sxs-lookup"><span data-stu-id="f05a8-130">Error</span></span>  
  
-   <span data-ttu-id="f05a8-131">重試</span><span class="sxs-lookup"><span data-stu-id="f05a8-131">Retry</span></span>  
  
-   <span data-ttu-id="f05a8-132">執行中</span><span class="sxs-lookup"><span data-stu-id="f05a8-132">Running</span></span>  
  
-   <span data-ttu-id="f05a8-133">Completed</span><span class="sxs-lookup"><span data-stu-id="f05a8-133">Completed</span></span>  
  
 <span data-ttu-id="f05a8-134">**發行集**</span><span class="sxs-lookup"><span data-stu-id="f05a8-134">**Publication**</span></span>  
 <span data-ttu-id="f05a8-135">與代理程式相關聯之發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="f05a8-135">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="f05a8-136">**上次啟動時間**</span><span class="sxs-lookup"><span data-stu-id="f05a8-136">**Last Start Time**</span></span>  
 <span data-ttu-id="f05a8-137">代理程式上次啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="f05a8-137">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="f05a8-138">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="f05a8-138">**Duration**</span></span>  
 <span data-ttu-id="f05a8-139">代理程式已執行的時間長度。</span><span class="sxs-lookup"><span data-stu-id="f05a8-139">The length of time the agent has run.</span></span> <span data-ttu-id="f05a8-140">如果代理程式目前正在執行，此時間代表經過時間。如果代理程式先前已執行過，則代表總時間。</span><span class="sxs-lookup"><span data-stu-id="f05a8-140">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="f05a8-141">**最後一個動作**</span><span class="sxs-lookup"><span data-stu-id="f05a8-141">**Last Action**</span></span>  
 <span data-ttu-id="f05a8-142">最近一次代理程式執行期間執行的最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="f05a8-142">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="f05a8-143">**傳遞速率**</span><span class="sxs-lookup"><span data-stu-id="f05a8-143">**Delivery Rate**</span></span>  
 <span data-ttu-id="f05a8-144">最近一次代理程式執行期間，在散發資料庫中認可初始化命令的速率 (以每秒命令數為單位)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-144">The rate, in commands per second, at which initialization commands are committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="f05a8-145">**交易數**</span><span class="sxs-lookup"><span data-stu-id="f05a8-145">**#Trans**</span></span>  
 <span data-ttu-id="f05a8-146">最近一次代理程式執行期間，在散發資料庫中認可的交易數目。</span><span class="sxs-lookup"><span data-stu-id="f05a8-146">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="f05a8-147">**命令數**</span><span class="sxs-lookup"><span data-stu-id="f05a8-147">**#Cmds**</span></span>  
 <span data-ttu-id="f05a8-148">最近一次代理程式執行期間，在散發資料庫中認可的命令數目。</span><span class="sxs-lookup"><span data-stu-id="f05a8-148">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="f05a8-149">命令就相當於資料變更，例如更新。</span><span class="sxs-lookup"><span data-stu-id="f05a8-149">A command is equivalent to a data change, such as an update.</span></span>  
  
### <a name="log-reader-agent"></a><span data-ttu-id="f05a8-150">記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="f05a8-150">Log Reader Agent</span></span>  
 <span data-ttu-id="f05a8-151">**狀態**</span><span class="sxs-lookup"><span data-stu-id="f05a8-151">**Status**</span></span>  
 <span data-ttu-id="f05a8-152">代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="f05a8-152">The status of the agent.</span></span> <span data-ttu-id="f05a8-153">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="f05a8-153">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="f05a8-154">錯誤</span><span class="sxs-lookup"><span data-stu-id="f05a8-154">Error</span></span>  
  
-   <span data-ttu-id="f05a8-155">重試</span><span class="sxs-lookup"><span data-stu-id="f05a8-155">Retry</span></span>  
  
-   <span data-ttu-id="f05a8-156">執行中</span><span class="sxs-lookup"><span data-stu-id="f05a8-156">Running</span></span>  
  
-   <span data-ttu-id="f05a8-157">未執行</span><span class="sxs-lookup"><span data-stu-id="f05a8-157">Not running</span></span>  
  
 <span data-ttu-id="f05a8-158">**發行集資料庫**</span><span class="sxs-lookup"><span data-stu-id="f05a8-158">**Publication Database**</span></span>  
 <span data-ttu-id="f05a8-159">與代理程式相關聯之發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="f05a8-159">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="f05a8-160">**上次啟動時間**</span><span class="sxs-lookup"><span data-stu-id="f05a8-160">**Last Start Time**</span></span>  
 <span data-ttu-id="f05a8-161">代理程式上次啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="f05a8-161">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="f05a8-162">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="f05a8-162">**Duration**</span></span>  
 <span data-ttu-id="f05a8-163">代理程式已執行的時間長度。</span><span class="sxs-lookup"><span data-stu-id="f05a8-163">The length of time the agent has run.</span></span> <span data-ttu-id="f05a8-164">如果代理程式目前正在執行，此時間代表經過時間。如果代理程式先前已執行過，則代表總時間。</span><span class="sxs-lookup"><span data-stu-id="f05a8-164">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="f05a8-165">**最後一個動作**</span><span class="sxs-lookup"><span data-stu-id="f05a8-165">**Last Action**</span></span>  
 <span data-ttu-id="f05a8-166">最近一次代理程式執行期間執行的最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="f05a8-166">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="f05a8-167">**傳遞速率**</span><span class="sxs-lookup"><span data-stu-id="f05a8-167">**Delivery Rate**</span></span>  
 <span data-ttu-id="f05a8-168">在散發資料庫中認可變更的速率 (以每秒命令數為單位)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-168">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="f05a8-169">**延遲**</span><span class="sxs-lookup"><span data-stu-id="f05a8-169">**Latency**</span></span>  
 <span data-ttu-id="f05a8-170">在發行集資料庫中認可的最近一次變更與散發資料庫中認可的對應命令之間經過的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-170">The amount of time, in seconds, that has elapsed between the most recent change being committed in the publication database, and the corresponding command being committed in the distribution database.</span></span>  
  
 <span data-ttu-id="f05a8-171">**交易數**</span><span class="sxs-lookup"><span data-stu-id="f05a8-171">**#Trans**</span></span>  
 <span data-ttu-id="f05a8-172">最近一次代理程式執行期間，在散發資料庫中認可的交易數目。</span><span class="sxs-lookup"><span data-stu-id="f05a8-172">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="f05a8-173">**命令數**</span><span class="sxs-lookup"><span data-stu-id="f05a8-173">**#Cmds**</span></span>  
 <span data-ttu-id="f05a8-174">最近一次代理程式執行期間，在散發資料庫中認可的命令數目。</span><span class="sxs-lookup"><span data-stu-id="f05a8-174">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="f05a8-175">命令就相當於資料變更，例如更新。</span><span class="sxs-lookup"><span data-stu-id="f05a8-175">A command is equivalent to a data change, such as an update.</span></span>  
  
 <span data-ttu-id="f05a8-176">**平均命令數**</span><span class="sxs-lookup"><span data-stu-id="f05a8-176">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="f05a8-177">最近一次代理程式執行期間，每項交易的平均命令數目。</span><span class="sxs-lookup"><span data-stu-id="f05a8-177">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="queue-reader-agent"></a><span data-ttu-id="f05a8-178">佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="f05a8-178">Queue Reader Agent</span></span>  
 <span data-ttu-id="f05a8-179">**狀態**</span><span class="sxs-lookup"><span data-stu-id="f05a8-179">**Status**</span></span>  
 <span data-ttu-id="f05a8-180">代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="f05a8-180">The status of the agent.</span></span> <span data-ttu-id="f05a8-181">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="f05a8-181">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="f05a8-182">錯誤</span><span class="sxs-lookup"><span data-stu-id="f05a8-182">Error</span></span>  
  
-   <span data-ttu-id="f05a8-183">重試</span><span class="sxs-lookup"><span data-stu-id="f05a8-183">Retry</span></span>  
  
-   <span data-ttu-id="f05a8-184">執行中</span><span class="sxs-lookup"><span data-stu-id="f05a8-184">Running</span></span>  
  
-   <span data-ttu-id="f05a8-185">未執行</span><span class="sxs-lookup"><span data-stu-id="f05a8-185">Not running</span></span>  
  
 <span data-ttu-id="f05a8-186">**散發資料庫**</span><span class="sxs-lookup"><span data-stu-id="f05a8-186">**Distribution Database**</span></span>  
 <span data-ttu-id="f05a8-187">與代理程式相關聯之散發資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="f05a8-187">The name of the distribution database with which the agent is associated.</span></span>  
  
 <span data-ttu-id="f05a8-188">**上次啟動時間**</span><span class="sxs-lookup"><span data-stu-id="f05a8-188">**Last Start Time**</span></span>  
 <span data-ttu-id="f05a8-189">代理程式上次啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="f05a8-189">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="f05a8-190">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="f05a8-190">**Duration**</span></span>  
 <span data-ttu-id="f05a8-191">代理程式已執行的時間長度。</span><span class="sxs-lookup"><span data-stu-id="f05a8-191">The length of time the agent has run.</span></span> <span data-ttu-id="f05a8-192">如果代理程式目前正在執行，此時間代表經過時間；如果代理程式是先前有執行過，則此時間代表總共時間。</span><span class="sxs-lookup"><span data-stu-id="f05a8-192">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="f05a8-193">**最後一個動作**</span><span class="sxs-lookup"><span data-stu-id="f05a8-193">**Last Action**</span></span>  
 <span data-ttu-id="f05a8-194">最近一次代理程式執行期間執行的最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="f05a8-194">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="f05a8-195">**傳遞速率**</span><span class="sxs-lookup"><span data-stu-id="f05a8-195">**Delivery Rate**</span></span>  
 <span data-ttu-id="f05a8-196">在散發資料庫中認可變更的速率 (以每秒命令數為單位)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-196">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="f05a8-197">**延遲**</span><span class="sxs-lookup"><span data-stu-id="f05a8-197">**Latency**</span></span>  
 <span data-ttu-id="f05a8-198">在訂閱資料庫中認可的最近一次變更與發行集資料庫中認可的對應命令之間經過的時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="f05a8-198">The amount of time, in seconds, that has elapsed between the most recent change being committed in a subscription database, and the corresponding command being committed in the publication database.</span></span>  
  
 <span data-ttu-id="f05a8-199">**交易數**</span><span class="sxs-lookup"><span data-stu-id="f05a8-199">**#Trans**</span></span>  
 <span data-ttu-id="f05a8-200">最近一次代理程式執行期間，在發行集資料庫中認可的交易數目。</span><span class="sxs-lookup"><span data-stu-id="f05a8-200">The number of transactions committed in the publication database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="f05a8-201">**命令數**</span><span class="sxs-lookup"><span data-stu-id="f05a8-201">**#Cmds**</span></span>  
 <span data-ttu-id="f05a8-202">最近一次代理程式執行期間，在發行集資料庫中認可的命令數目。</span><span class="sxs-lookup"><span data-stu-id="f05a8-202">The number of commands committed in the publication database during the most recent run of the agent.</span></span> <span data-ttu-id="f05a8-203">命令就相當於資料變更，例如更新。</span><span class="sxs-lookup"><span data-stu-id="f05a8-203">A command is equivalent to a data change, such as an update.</span></span>  
  
 <span data-ttu-id="f05a8-204">**平均命令數**</span><span class="sxs-lookup"><span data-stu-id="f05a8-204">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="f05a8-205">最近一次代理程式執行期間，每項交易的平均命令數目。</span><span class="sxs-lookup"><span data-stu-id="f05a8-205">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="maintenance-jobs"></a><span data-ttu-id="f05a8-206">維護作業</span><span class="sxs-lookup"><span data-stu-id="f05a8-206">Maintenance Jobs</span></span>  
 <span data-ttu-id="f05a8-207">**狀態**</span><span class="sxs-lookup"><span data-stu-id="f05a8-207">**Status**</span></span>  
 <span data-ttu-id="f05a8-208">每一個作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="f05a8-208">The status of each job.</span></span> <span data-ttu-id="f05a8-209">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="f05a8-209">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="f05a8-210">錯誤</span><span class="sxs-lookup"><span data-stu-id="f05a8-210">Error</span></span>  
  
-   <span data-ttu-id="f05a8-211">重試</span><span class="sxs-lookup"><span data-stu-id="f05a8-211">Retry</span></span>  
  
-   <span data-ttu-id="f05a8-212">執行中</span><span class="sxs-lookup"><span data-stu-id="f05a8-212">Running</span></span>  
  
-   <span data-ttu-id="f05a8-213">未執行</span><span class="sxs-lookup"><span data-stu-id="f05a8-213">Not running</span></span>  
  
 <span data-ttu-id="f05a8-214">**作業**</span><span class="sxs-lookup"><span data-stu-id="f05a8-214">**Job**</span></span>  
 <span data-ttu-id="f05a8-215">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="f05a8-215">The name of the job.</span></span>  
  
 <span data-ttu-id="f05a8-216">**上次啟動時間**</span><span class="sxs-lookup"><span data-stu-id="f05a8-216">**Last Start Time**</span></span>  
 <span data-ttu-id="f05a8-217">作業上次啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="f05a8-217">The last time at which the job started.</span></span>  
  
 <span data-ttu-id="f05a8-218">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="f05a8-218">**Duration**</span></span>  
 <span data-ttu-id="f05a8-219">作業已執行的時間長度。</span><span class="sxs-lookup"><span data-stu-id="f05a8-219">The length of time the job has run.</span></span> <span data-ttu-id="f05a8-220">如果作業目前正在執行，此時間代表經過時間。如果作業先前已執行過，則代表總時間。</span><span class="sxs-lookup"><span data-stu-id="f05a8-220">The time represents elapsed time if the job is currently running, and total time if the job has run previously.</span></span>  
  
 <span data-ttu-id="f05a8-221">**最後一個動作**</span><span class="sxs-lookup"><span data-stu-id="f05a8-221">**Last Action**</span></span>  
 <span data-ttu-id="f05a8-222">最近一次作業執行期間執行的最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="f05a8-222">The last action performed during the most recent run of the job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05a8-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f05a8-223">See Also</span></span>  
 <span data-ttu-id="f05a8-224">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="f05a8-224">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="f05a8-225">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="f05a8-225">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="f05a8-226">監視複寫</span><span class="sxs-lookup"><span data-stu-id="f05a8-226">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
