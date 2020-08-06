---
title: SQL Server 複寫 [散發者資訊] 對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.Distributor.Publications.f1
- sql12.rep.monitor.Distributor.commonjobs..f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.merge.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.snapshot.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.tran.f1
ms.assetid: 1f499277-7f12-42ba-8cf4-52b683434944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ca0717a63c9660c225ec238e1e4d2423f7d01ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585867"
---
# <a name="distributor-information-dialog-box"></a><span data-ttu-id="0bc34-102">散發者資訊對話方塊</span><span class="sxs-lookup"><span data-stu-id="0bc34-102">Distributor Information Dialog Box</span></span> 
<span data-ttu-id="0bc34-103">本主題**提供 [散發**者] 對話方塊的相關資訊</span><span class="sxs-lookup"><span data-stu-id="0bc34-103">This topic provides information on the **Distributor** dialog box</span></span> 

## <a name="publications"></a><span data-ttu-id="0bc34-104">發行集</span><span class="sxs-lookup"><span data-stu-id="0bc34-104">Publications</span></span>

  <span data-ttu-id="0bc34-105">**[發行集]** 索引標籤可以提供在左窗格中所選取「散發者」之所有發行集的摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="0bc34-105">The **Publications** tab provides summary information for all publications at the Distributor that is selected in the left pane.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0bc34-106">選項</span><span class="sxs-lookup"><span data-stu-id="0bc34-106">Options</span></span>  
 <span data-ttu-id="0bc34-107">顯示的資訊會與受到「散發者」支援的發行集相關，當中包括了包含「發行者」之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料行。</span><span class="sxs-lookup"><span data-stu-id="0bc34-107">The information that is displayed about the publications supported by the Distributor includes a column that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span> <span data-ttu-id="0bc34-108">否則，當您在複寫監視器的「發行者」檢視中檢視發行集時，所提供的發行集資訊會與此處的發行集資訊相同。</span><span class="sxs-lookup"><span data-stu-id="0bc34-108">Otherwise, the publication information is the same as the publication information that is provided when you view publications in the Publisher view of Replication Monitor.</span></span> <span data-ttu-id="0bc34-109">如需有關 **[發行集]** 索引標籤中之資料行的詳細資訊，請參閱＜ [Publisher Information, Publications](publisher-information-publications.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0bc34-109">For more information about the columns in the **Publications** tab, see [Publisher Information, Publications](publisher-information-publications.md).</span></span>  

## <a name="subscription-watch-list"></a><span data-ttu-id="0bc34-110">訂閱監看清單</span><span class="sxs-lookup"><span data-stu-id="0bc34-110">Subscription watch list</span></span>

### <a name="transactional-replication"></a><span data-ttu-id="0bc34-111">異動複寫</span><span class="sxs-lookup"><span data-stu-id="0bc34-111">Transactional replication</span></span> 
  <span data-ttu-id="0bc34-112">交易式訂閱資訊會包括「發行者」的名稱。</span><span class="sxs-lookup"><span data-stu-id="0bc34-112">Information for transactional subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="0bc34-113">否則，這個對話方塊提供的功能和資訊會與在「發行者」檢視相同。</span><span class="sxs-lookup"><span data-stu-id="0bc34-113">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="0bc34-114">如需如何使用這個對話方塊的詳細資訊，請參閱[發行者資訊、訂閱監看清單 &#40;交易式發行集，SQL Server 2005 和更新版本&#41;](publisher-information-subscription-watch-list-transactional.md)。</span><span class="sxs-lookup"><span data-stu-id="0bc34-114">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Transactional Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-transactional.md).</span></span>  

### <a name="merge-replication"></a><span data-ttu-id="0bc34-115">合併式複寫</span><span class="sxs-lookup"><span data-stu-id="0bc34-115">Merge replication</span></span>
  <span data-ttu-id="0bc34-116">合併式發行集的訂閱資訊會包括「發行者」的名稱。</span><span class="sxs-lookup"><span data-stu-id="0bc34-116">Information for merge publication subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="0bc34-117">否則，這個對話方塊提供的功能和資訊會與在「發行者」檢視相同。</span><span class="sxs-lookup"><span data-stu-id="0bc34-117">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="0bc34-118">如需如何使用這個對話方塊的詳細資訊，請參閱[發行者資訊、訂閱監看清單 &#40;合併式發行集，SQL Server 2005 和更新版本&#41;](publisher-information-subscription-watch-list-merge-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="0bc34-118">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Merge Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-merge-publication.md).</span></span> 

### <a name="snapshot-replication"></a><span data-ttu-id="0bc34-119">快照式複寫</span><span class="sxs-lookup"><span data-stu-id="0bc34-119">Snapshot replication</span></span>
  <span data-ttu-id="0bc34-120">快照式發行集的訂閱資訊會包括「發行者」的名稱。</span><span class="sxs-lookup"><span data-stu-id="0bc34-120">Information for snapshot publication subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="0bc34-121">否則，這個對話方塊提供的功能和資訊會與在「發行者」檢視相同。</span><span class="sxs-lookup"><span data-stu-id="0bc34-121">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="0bc34-122">如需如何使用這個對話方塊的詳細資訊，請參閱[發行者資訊、訂閱監看清單 &#40;快照式發行集，SQL Server 2005 和更新版本&#41;](publisher-information-subscription-watch-list-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="0bc34-122">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Snapshot Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-snapshot.md).</span></span>  

## <a name="agents"></a><span data-ttu-id="0bc34-123">代理程式</span><span class="sxs-lookup"><span data-stu-id="0bc34-123">Agents</span></span>
  <span data-ttu-id="0bc34-124">**[代理程式]** 索引標籤會顯示與發行者和訂閱者相關聯之代理程式和維護作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0bc34-124">The **Agents** tab displays information about the agents and maintenance jobs that are associated with the Publisher and Subscriber.</span></span>  
  
 <span data-ttu-id="0bc34-125">專供「散發者」檢視中的「散發者」使用的代理程式會位於 **[代理程式]** 索引標籤中，當中包含了可供「發行者」使用且位於 **[代理程式]** 索引標籤中的所有代理程式。</span><span class="sxs-lookup"><span data-stu-id="0bc34-125">The agents that are available in the **Agents** tab for a Distributor in Distributor view include all the agents that are available in the **Agents** tab for a Publisher.</span></span> <span data-ttu-id="0bc34-126">但是，專供「散發者」檢視中之「散發者」使用的 **[代理程式]** 索引標籤也會包含「散發者代理程式」和「合併代理程式」。</span><span class="sxs-lookup"><span data-stu-id="0bc34-126">However, the **Agents** tab for a Distributor in Distributor view also includes a Distributor Agent and a Merge Agent.</span></span>  
  
 <span data-ttu-id="0bc34-127">如需有關「快照集」、「佇列讀取器代理程式」和維護作業的詳細資訊，請參閱＜ [Publisher Information, Agents](publisher-information-agents.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0bc34-127">For more information about the Snapshot, Log Reader, and Queue Reader agents, and maintenance jobs, see [Publisher Information, Agents](publisher-information-agents.md).</span></span> <span data-ttu-id="0bc34-128">請注意，當您在 **[代理程式]** 索引標籤上檢視「散發者」的代理程式資訊時，「發行者」資訊也會顯示，以供「快照集」和「記錄讀取器」代理程式使用。</span><span class="sxs-lookup"><span data-stu-id="0bc34-128">Notice that when you are viewing agent information on the **Agents** tab for a Distributor, Publisher information is present for the Snapshot and Log Reader agents.</span></span> <span data-ttu-id="0bc34-129">但是，在專供「散發者」檢視中之「散發者」使用的 **[代理程式]** 索引標籤中，您也可以選取 **[散發者代理程式]** 和 **[合併代理程式]**。</span><span class="sxs-lookup"><span data-stu-id="0bc34-129">However, in the **Agents** tab for a Distributor in Distributor view, you can also select **Distributor Agent** and **Merge Agent**.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0bc34-130">選項</span><span class="sxs-lookup"><span data-stu-id="0bc34-130">Options</span></span>  
 <span data-ttu-id="0bc34-131">下列各節將描述這個索引標籤上針對「散發者代理程式」和「合併代理程式」顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="0bc34-131">The following sections describe the data that is displayed on this tab for the Distributor Agent and Merge Agent.</span></span>  
  
### <a name="distributor-agent"></a><span data-ttu-id="0bc34-132">[散發者代理程式]</span><span class="sxs-lookup"><span data-stu-id="0bc34-132">Distributor Agent</span></span>  
 <span data-ttu-id="0bc34-133">**狀態**</span><span class="sxs-lookup"><span data-stu-id="0bc34-133">**Status**</span></span>  
 <span data-ttu-id="0bc34-134">代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="0bc34-134">The status of the agent.</span></span> <span data-ttu-id="0bc34-135">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="0bc34-135">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="0bc34-136">錯誤</span><span class="sxs-lookup"><span data-stu-id="0bc34-136">Error</span></span>    
-   <span data-ttu-id="0bc34-137">重試</span><span class="sxs-lookup"><span data-stu-id="0bc34-137">Retry</span></span>    
-   <span data-ttu-id="0bc34-138">執行中</span><span class="sxs-lookup"><span data-stu-id="0bc34-138">Running</span></span>    
-   <span data-ttu-id="0bc34-139">未執行</span><span class="sxs-lookup"><span data-stu-id="0bc34-139">Not Running</span></span>    
-   <span data-ttu-id="0bc34-140">從未啟動</span><span class="sxs-lookup"><span data-stu-id="0bc34-140">Never started</span></span>  
  
 <span data-ttu-id="0bc34-141">**發行者**</span><span class="sxs-lookup"><span data-stu-id="0bc34-141">**Publisher**</span></span>  
 <span data-ttu-id="0bc34-142">「發行者」的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bc34-142">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span>  
  
 <span data-ttu-id="0bc34-143">**發行**</span><span class="sxs-lookup"><span data-stu-id="0bc34-143">**Publication**</span></span>  
 <span data-ttu-id="0bc34-144">與代理程式相關聯之發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="0bc34-144">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="0bc34-145">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="0bc34-145">**Subscription**</span></span>  
 <span data-ttu-id="0bc34-146">訂閱的名稱，格式應該為：[*SubscriberName*].[*Database*]。</span><span class="sxs-lookup"><span data-stu-id="0bc34-146">The name of the subscription, in the form: [*SubscriberName*].[*Database*].</span></span>  
  
 <span data-ttu-id="0bc34-147">**型別**</span><span class="sxs-lookup"><span data-stu-id="0bc34-147">**Type**</span></span>  
 <span data-ttu-id="0bc34-148">複寫類型：發送、提取或匿名。</span><span class="sxs-lookup"><span data-stu-id="0bc34-148">Type of replication: push, pull, or Anonymous.</span></span>  
  
 <span data-ttu-id="0bc34-149">**上次啟動時間**</span><span class="sxs-lookup"><span data-stu-id="0bc34-149">**Last Start Time**</span></span>  
 <span data-ttu-id="0bc34-150">代理程式上次啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="0bc34-150">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="0bc34-151">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="0bc34-151">**Duration**</span></span>  
 <span data-ttu-id="0bc34-152">代理程式已執行的時間長度。</span><span class="sxs-lookup"><span data-stu-id="0bc34-152">The length of time that the agent has run.</span></span> <span data-ttu-id="0bc34-153">如果代理程式目前正在執行，此時間代表經過時間。如果代理程式先前已執行過，則代表總時間。</span><span class="sxs-lookup"><span data-stu-id="0bc34-153">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="0bc34-154">**最後一個動作**</span><span class="sxs-lookup"><span data-stu-id="0bc34-154">**Last Action**</span></span>  
 <span data-ttu-id="0bc34-155">代理程式最近一次執行期間執行的最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="0bc34-155">The last action that was performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="0bc34-156">**傳遞速率**</span><span class="sxs-lookup"><span data-stu-id="0bc34-156">**Delivery Rate**</span></span>  
 <span data-ttu-id="0bc34-157">最近一次代理程式執行期間，在散發資料庫中認可初始化命令的速率 (以每秒命令數為單位)。</span><span class="sxs-lookup"><span data-stu-id="0bc34-157">The rate, in commands per second, at which initialization commands are committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="0bc34-158">**延遲**</span><span class="sxs-lookup"><span data-stu-id="0bc34-158">**Latency**</span></span>  
 <span data-ttu-id="0bc34-159">在發行集資料庫中認可的最近一次變更與散發資料庫中認可的對應命令之間經過的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="0bc34-159">The time, in seconds, that has elapsed between the most recent change being committed in the publication database, and the corresponding command being committed in the distribution database.</span></span>  
  
 <span data-ttu-id="0bc34-160">**交易數**</span><span class="sxs-lookup"><span data-stu-id="0bc34-160">**#Trans**</span></span>  
 <span data-ttu-id="0bc34-161">最近一次代理程式執行期間，在散發資料庫中認可的交易數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-161">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="0bc34-162">**命令數**</span><span class="sxs-lookup"><span data-stu-id="0bc34-162">**#Cmds**</span></span>  
 <span data-ttu-id="0bc34-163">最近一次代理程式執行期間，在散發資料庫中認可的命令數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-163">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="0bc34-164">命令與資料變更 (例如更新) 相同。</span><span class="sxs-lookup"><span data-stu-id="0bc34-164">A command is the same as a data change, such as an update.</span></span>  
  
 <span data-ttu-id="0bc34-165">**平均命令數**</span><span class="sxs-lookup"><span data-stu-id="0bc34-165">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="0bc34-166">最近一次代理程式執行期間，每項交易的平均命令數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-166">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="merge-agent"></a><span data-ttu-id="0bc34-167">合併代理程式</span><span class="sxs-lookup"><span data-stu-id="0bc34-167">Merge Agent</span></span>  
 <span data-ttu-id="0bc34-168">**狀態**</span><span class="sxs-lookup"><span data-stu-id="0bc34-168">**Status**</span></span>  
 <span data-ttu-id="0bc34-169">代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="0bc34-169">The status of the agent.</span></span> <span data-ttu-id="0bc34-170">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="0bc34-170">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="0bc34-171">錯誤</span><span class="sxs-lookup"><span data-stu-id="0bc34-171">Error</span></span>    
-   <span data-ttu-id="0bc34-172">重試</span><span class="sxs-lookup"><span data-stu-id="0bc34-172">Retry</span></span>    
-   <span data-ttu-id="0bc34-173">執行中</span><span class="sxs-lookup"><span data-stu-id="0bc34-173">Running</span></span>    
-   <span data-ttu-id="0bc34-174">未執行</span><span class="sxs-lookup"><span data-stu-id="0bc34-174">Not Running</span></span>    
-   <span data-ttu-id="0bc34-175">從未啟動</span><span class="sxs-lookup"><span data-stu-id="0bc34-175">Never started</span></span>  
  
 <span data-ttu-id="0bc34-176">**發行者**</span><span class="sxs-lookup"><span data-stu-id="0bc34-176">**Publisher**</span></span>  
 <span data-ttu-id="0bc34-177">「發行者」的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bc34-177">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span>  
  
 <span data-ttu-id="0bc34-178">**發行**</span><span class="sxs-lookup"><span data-stu-id="0bc34-178">**Publication**</span></span>  
 <span data-ttu-id="0bc34-179">與代理程式相關聯之發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="0bc34-179">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="0bc34-180">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="0bc34-180">**Subscription**</span></span>  
 <span data-ttu-id="0bc34-181">訂閱的名稱，格式應該為：[*SubscriberName*].[*Database*]。</span><span class="sxs-lookup"><span data-stu-id="0bc34-181">The name of the subscription, in the form: [*SubscriberName*].[*Database*].</span></span>  
  
 <span data-ttu-id="0bc34-182">**型別**</span><span class="sxs-lookup"><span data-stu-id="0bc34-182">**Type**</span></span>  
 <span data-ttu-id="0bc34-183">複寫類型：發送、提取或匿名。</span><span class="sxs-lookup"><span data-stu-id="0bc34-183">Type of replication: push, pull, or Anonymous.</span></span>  
  
 <span data-ttu-id="0bc34-184">**上次啟動時間**</span><span class="sxs-lookup"><span data-stu-id="0bc34-184">**Last Start Time**</span></span>  
 <span data-ttu-id="0bc34-185">代理程式上次啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="0bc34-185">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="0bc34-186">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="0bc34-186">**Duration**</span></span>  
 <span data-ttu-id="0bc34-187">代理程式已執行的時間長度。</span><span class="sxs-lookup"><span data-stu-id="0bc34-187">The length of time that the agent has run.</span></span> <span data-ttu-id="0bc34-188">如果代理程式目前正在執行，此時間代表經過時間。如果代理程式先前已執行過，則代表總時間。</span><span class="sxs-lookup"><span data-stu-id="0bc34-188">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="0bc34-189">**最後一個動作**</span><span class="sxs-lookup"><span data-stu-id="0bc34-189">**Last Action**</span></span>  
 <span data-ttu-id="0bc34-190">代理程式最近一次執行期間執行的最後一個動作。</span><span class="sxs-lookup"><span data-stu-id="0bc34-190">The last action that was performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="0bc34-191">**傳遞速率**</span><span class="sxs-lookup"><span data-stu-id="0bc34-191">**Delivery Rate**</span></span>  
 <span data-ttu-id="0bc34-192">在散發資料庫中認可變更的速率 (以每秒命令數為單位)。</span><span class="sxs-lookup"><span data-stu-id="0bc34-192">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="0bc34-193">**發行者插入**</span><span class="sxs-lookup"><span data-stu-id="0bc34-193">**Publisher Inserts**</span></span>  
 <span data-ttu-id="0bc34-194">發行者端所套用的 INSERT 命令數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-194">Number of INSERT commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="0bc34-195">**發行者更新**</span><span class="sxs-lookup"><span data-stu-id="0bc34-195">**Publisher Updates**</span></span>  
 <span data-ttu-id="0bc34-196">發行者端所套用的 UPDATE 命令數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-196">Number of UPDATE commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="0bc34-197">**發行者刪除**</span><span class="sxs-lookup"><span data-stu-id="0bc34-197">**Publisher Deletes**</span></span>  
 <span data-ttu-id="0bc34-198">發行者端所套用的 DELETE 命令數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-198">Number of DELETE commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="0bc34-199">**發行者衝突**</span><span class="sxs-lookup"><span data-stu-id="0bc34-199">**Publisher Conflicts**</span></span>  
 <span data-ttu-id="0bc34-200">合併處理期間發行者端每秒所發生的衝突數。</span><span class="sxs-lookup"><span data-stu-id="0bc34-200">The number of conflicts occurring at the Publisher during the merge process.</span></span>  
  
 <span data-ttu-id="0bc34-201">**訂閱者插入**</span><span class="sxs-lookup"><span data-stu-id="0bc34-201">**Subscriber Inserts**</span></span>  
 <span data-ttu-id="0bc34-202">訂閱者端所套用的 INSERT 命令數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-202">Number of INSERT commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="0bc34-203">**訂閱者更新**</span><span class="sxs-lookup"><span data-stu-id="0bc34-203">**Subscriber Updates**</span></span>  
 <span data-ttu-id="0bc34-204">訂閱者端所套用的 UPDATE 命令數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-204">Number of UPDATE commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="0bc34-205">**訂閱者刪除**</span><span class="sxs-lookup"><span data-stu-id="0bc34-205">**Subscriber Deletes**</span></span>  
 <span data-ttu-id="0bc34-206">訂閱者端所套用的 DELETE 命令數目。</span><span class="sxs-lookup"><span data-stu-id="0bc34-206">Number of DELETE commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="0bc34-207">**訂閱者衝突**</span><span class="sxs-lookup"><span data-stu-id="0bc34-207">**Subscriber Conflicts**</span></span>  
 <span data-ttu-id="0bc34-208">合併處理期間訂閱者端每秒所發生的衝突數。</span><span class="sxs-lookup"><span data-stu-id="0bc34-208">The number of conflicts occurring at the Subscriber during the merge process.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="0bc34-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bc34-209">See Also</span></span>  
 <span data-ttu-id="0bc34-210">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0bc34-210">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="0bc34-211">監視複寫</span><span class="sxs-lookup"><span data-stu-id="0bc34-211">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
