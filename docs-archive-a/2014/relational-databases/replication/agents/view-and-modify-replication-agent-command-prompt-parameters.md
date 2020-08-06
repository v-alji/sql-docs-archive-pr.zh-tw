---
title: 查看及修改複寫代理程式命令提示字元參數 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 752f674c21bb66c7b64e399e30e4917512431195
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585893"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a><span data-ttu-id="16812-102">檢視並修改複寫代理程式命令提示字元參數 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="16812-102">View and Modify Replication Agent Command Prompt Parameters (SQL Server Management Studio)</span></span>
  <span data-ttu-id="16812-103">複寫代理程式為可接受命令行參數的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="16812-103">Replication agents are executables that accept command line parameters.</span></span> <span data-ttu-id="16812-104">根據預設，代理程式會在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理程式作業步驟下執行，因此這些參數可以使用 [作業屬性 - \<Job>] 對話方塊進行檢視並修改。</span><span class="sxs-lookup"><span data-stu-id="16812-104">By default, agents run under [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job steps, so these parameters can be viewed and modified using the **Job Properties - \<Job>** dialog box.</span></span> <span data-ttu-id="16812-105">**的** [作業] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 資料夾及複寫監視器的 **[代理程式]** 索引標籤會提供此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="16812-105">This dialog box is available from the **Jobs** folder in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor.</span></span> <span data-ttu-id="16812-106">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="16812-106">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16812-107">代理程式參數變更會在代理程式下次啟動時生效。</span><span class="sxs-lookup"><span data-stu-id="16812-107">Agent parameter changes take effect the next time the agent is started.</span></span> <span data-ttu-id="16812-108">如果代理程式連續執行，則必須停止代理程式，然後重新啟動它。</span><span class="sxs-lookup"><span data-stu-id="16812-108">If the agent runs continuously, you must stop and restart the agent.</span></span>  
  
 <span data-ttu-id="16812-109">雖然可以直接修改參數，但是在更多的情形下透過代理程式設定檔來對其進行修改。</span><span class="sxs-lookup"><span data-stu-id="16812-109">Although parameters can be modified directly, it is more common to modify them through an agent profile.</span></span> <span data-ttu-id="16812-110">如需相關資訊，請參閱 [Replication Agent Profiles](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="16812-110">For more information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="16812-111">如果您從 **[作業]** 資料夾存取代理程式作業，則使用下表來決定可用於各代理程式的代理程式作業名稱與參數。</span><span class="sxs-lookup"><span data-stu-id="16812-111">If you access agent jobs from the **Jobs** folder, use the following table to determine the agent job name and the parameters available for each agent.</span></span>  
  
|<span data-ttu-id="16812-112">代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-112">Agent</span></span>|<span data-ttu-id="16812-113">作業名稱</span><span class="sxs-lookup"><span data-stu-id="16812-113">Job name</span></span>|<span data-ttu-id="16812-114">如需參數清單，請參閱...</span><span class="sxs-lookup"><span data-stu-id="16812-114">For a list of parameters, see...</span></span>|  
|-----------|--------------|------------------------------------|  
|<span data-ttu-id="16812-115">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-115">Snapshot Agent</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<integer>**|[<span data-ttu-id="16812-116">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="16812-116">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|  
|<span data-ttu-id="16812-117">合併式發行集分割區的快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-117">Snapshot Agent for a merge publication partition</span></span>|<span data-ttu-id="16812-118">**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**</span><span class="sxs-lookup"><span data-stu-id="16812-118">**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**</span></span>|[<span data-ttu-id="16812-119">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="16812-119">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|  
|<span data-ttu-id="16812-120">記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-120">Log Reader Agent</span></span>|**\<Publisher>-\<PublicationDatabase>-\<integer>**|[<span data-ttu-id="16812-121">複寫記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-121">Replication Log Reader Agent</span></span>](replication-log-reader-agent.md)|  
|<span data-ttu-id="16812-122">提取訂閱的合併代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-122">Merge Agent for pull subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|[<span data-ttu-id="16812-123">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="16812-123">Replication Merge Agent</span></span>](replication-merge-agent.md)|  
|<span data-ttu-id="16812-124">發送訂閱的合併代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-124">Merge Agent for push subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[<span data-ttu-id="16812-125">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="16812-125">Replication Merge Agent</span></span>](replication-merge-agent.md)|  
|<span data-ttu-id="16812-126">發送訂閱的散發代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-126">Distribution Agent for push subscriptions</span></span>|<span data-ttu-id="16812-127">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="16812-127">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span></span>|[<span data-ttu-id="16812-128">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="16812-128">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="16812-129">提取訂閱的散發代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-129">Distribution Agent for pull subscriptions</span></span>|<span data-ttu-id="16812-130">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="16812-130">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span></span>|[<span data-ttu-id="16812-131">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="16812-131">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="16812-132">發送訂閱至非 SQL Server 訂閱者的散發代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-132">Distribution Agent for push subscriptions to non-SQL Server Subscribers</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[<span data-ttu-id="16812-133">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="16812-133">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="16812-134">佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-134">Queue Reader Agent</span></span>|<span data-ttu-id="16812-135">**[\<Distributor>].\<integer>**</span><span class="sxs-lookup"><span data-stu-id="16812-135">**[\<Distributor>].\<integer>**</span></span>|[<span data-ttu-id="16812-136">複寫佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="16812-136">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)|  
  
 <span data-ttu-id="16812-137"><sup>1</sup> 要發送訂閱至 Oracle 發行集，其為 \*\*\<Publisher>-\<Publisher**> 而非 **\<Publisher>-\<PublicationDatabase>**</span><span class="sxs-lookup"><span data-stu-id="16812-137"><sup>1</sup> For push subscriptions to Oracle publications, it is \*\*\<Publisher>-\<Publisher**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
 <span data-ttu-id="16812-138"><sup>2</sup> 要發送訂閱至 Oracle 發行集，其為 \*\*\<Publisher>-\<DistributionDatabase**> 而非 **\<Publisher>-\<PublicationDatabase>**</span><span class="sxs-lookup"><span data-stu-id="16812-138"><sup>2</sup> For pull subscriptions to Oracle publications, it is \*\*\<Publisher>-\<DistributionDatabase**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a><span data-ttu-id="16812-139">若要從 Management Studio 檢視並修改複寫代理程式命令列參數</span><span class="sxs-lookup"><span data-stu-id="16812-139">To view and modify replication agent command line parameters from Management Studio</span></span>  
  
1.  <span data-ttu-id="16812-140">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中適當的電腦，然後展開伺服器節點：</span><span class="sxs-lookup"><span data-stu-id="16812-140">Connect to the appropriate computer in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node:</span></span>  
  
    -   <span data-ttu-id="16812-141">對於提取訂閱的「散發代理程式」與「合併代理程式」，則連接到「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="16812-141">For the Distribution Agent and Merge Agent for pull subscriptions, connect to the Subscriber.</span></span>  
  
    -   <span data-ttu-id="16812-142">對於所有其他代理程式，則連接到「散發者」。</span><span class="sxs-lookup"><span data-stu-id="16812-142">For all other agents, connect to the Distributor.</span></span>  
  
2.  <span data-ttu-id="16812-143">展開 **[SQL Server Agent]** 資料夾，然後展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="16812-143">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="16812-144">以滑鼠右鍵按一下作業，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="16812-144">Right-click a job, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="16812-145">在 [作業屬性 - \<Job>] 對話方塊的 [步驟] 頁面上，選取 [執行代理程式] 步驟，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="16812-145">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="16812-146">在 **[作業步驟屬性 - 執行代理程式]** 對話方塊中，編輯 **[命令]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="16812-146">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
6.  <span data-ttu-id="16812-147">同時在兩個對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="16812-147">Click **OK** on both dialog boxes.</span></span>  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a><span data-ttu-id="16812-148">若要從複寫監視器檢視並修改散發代理程式與合併代理程式命令列參數</span><span class="sxs-lookup"><span data-stu-id="16812-148">To view and modify Distribution Agent and Merge Agent command line parameters from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="16812-149">在複寫監視器的左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="16812-149">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="16812-150">按一下 **[所有訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="16812-150">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="16812-151">以滑鼠右鍵按一下訂閱，然後按一下 **[檢視詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="16812-151">Right-click a subscription, and then click **View Details**.</span></span>  
  
4.  <span data-ttu-id="16812-152">在 [**訂 \< SubscriptionName> **用帳戶] 視窗中，按一下 [**動作**]，然後按一下 [ \*\* \<AgentName> 作業屬性\*\*]。</span><span class="sxs-lookup"><span data-stu-id="16812-152">In the **Subscription \< SubscriptionName>** window, click **Action**, and then click **\<AgentName> Job Properties**.</span></span>  
  
5.  <span data-ttu-id="16812-153">在 [作業屬性 - \<Job>] 對話方塊的 [步驟] 頁面上，選取 [執行代理程式] 步驟，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="16812-153">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="16812-154">在 **[作業步驟屬性 - 執行代理程式]** 對話方塊中，編輯 **[命令]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="16812-154">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
7.  <span data-ttu-id="16812-155">同時在兩個對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="16812-155">Click **OK** on both dialog boxes.</span></span>  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a><span data-ttu-id="16812-156">若要從複寫監視器檢視並修改快照集代理程式、記錄讀取器代理程式與佇列讀取器代理程式命令列參數</span><span class="sxs-lookup"><span data-stu-id="16812-156">To view and modify Snapshot Agent, Log Reader Agent, and Queue Reader Agent command line parameters from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="16812-157">在複寫監視器的左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="16812-157">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="16812-158">按一下 **[代理程式]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="16812-158">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="16812-159">以滑鼠右鍵按一下方格內的代理程式，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="16812-159">Right-click an agent in the grid, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="16812-160">在 [作業屬性 - \<Job>] 對話方塊的 [步驟] 頁面上，選取 [執行代理程式] 步驟，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="16812-160">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="16812-161">在 **[作業步驟屬性 - 執行代理程式]** 對話方塊中，編輯 **[命令]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="16812-161">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
6.  <span data-ttu-id="16812-162">同時在兩個對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="16812-162">Click **OK** on both dialog boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16812-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16812-163">See Also</span></span>  
 <span data-ttu-id="16812-164">[複寫代理程式管理](replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="16812-164">[Replication Agent Administration](replication-agent-administration.md) </span></span>  
 <span data-ttu-id="16812-165">[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="16812-165">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) </span></span>  
 [<span data-ttu-id="16812-166">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="16812-166">Replication Agents Overview</span></span>](replication-agents-overview.md)  
  
  
