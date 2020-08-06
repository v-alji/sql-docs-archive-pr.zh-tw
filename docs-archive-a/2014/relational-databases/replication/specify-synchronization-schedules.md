---
title: 指定同步處理排程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], synchronizing
- scheduling synchronization [SQL Server replication]
- synchronization [SQL Server replication], schedules
- replication [SQL Server], synchronization
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d752817f7d620b2c6e5fdc5eeb2178c50c42040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706370"
---
# <a name="specify-synchronization-schedules"></a><span data-ttu-id="0799b-102">指定同步處理排程</span><span class="sxs-lookup"><span data-stu-id="0799b-102">Specify Synchronization Schedules</span></span>
  <span data-ttu-id="0799b-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中指定同步處理排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-103">This topic describes how to specify synchronization schedules in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="0799b-104">當您建立訂閱時，可以定義一個同步排程，以控制訂閱的複寫代理程式將於何時執行。</span><span class="sxs-lookup"><span data-stu-id="0799b-104">When you create a subscription, you can define a synchronization schedule that controls when the replication agent for the subscription will run.</span></span> <span data-ttu-id="0799b-105">如果不指定排程參數，訂閱將使用預設排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-105">If you do not specify scheduling parameters, the subscription will use the default schedule.</span></span>  
  
 <span data-ttu-id="0799b-106">訂閱是由散發代理程式 (適用於快照式與異動複寫) 或合併代理程式 (適用於合併式複寫) 同步處理。</span><span class="sxs-lookup"><span data-stu-id="0799b-106">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="0799b-107">代理程式可以繼續執行、視需要執行，或是依照排程執行。</span><span class="sxs-lookup"><span data-stu-id="0799b-107">Agents can run continuously, run on demand, or run on a schedule.</span></span>  
  
 <span data-ttu-id="0799b-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0799b-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0799b-109">**若要指定同步處理排程，請使用：**</span><span class="sxs-lookup"><span data-stu-id="0799b-109">**To specify synchronization schedules, using:**</span></span>  
  
     [<span data-ttu-id="0799b-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0799b-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0799b-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0799b-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="0799b-112">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="0799b-112">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0799b-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0799b-113">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="0799b-114">在「新增訂閱精靈」的 **[同步排程]** 頁面中指定同步排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-114">Specify synchronization schedules on the **Synchronization Schedule** page of the New Subscription Wizard.</span></span> <span data-ttu-id="0799b-115">如需有關存取這個精靈的詳細資訊，請參閱＜ [Create a Push Subscription](create-a-push-subscription.md) ＞與＜ [Create a Pull Subscription](create-a-pull-subscription.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0799b-115">For more information about accessing this wizard, see [Create a Push Subscription](create-a-push-subscription.md) and [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="0799b-116">在 **[作業排程屬性]** 對話方塊中修改同步處理排程，您可從 **的** [作業] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 資料夾和「複寫監視器」的代理程式詳細資料視窗中取得此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0799b-116">Modify synchronization schedules in the **Job Schedule Properties** dialog box, which is available from the **Jobs** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and from the agent details windows in Replication Monitor.</span></span> <span data-ttu-id="0799b-117">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-117">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="0799b-118">如果從 **[作業]** 資料夾指定排程，請使用下列資料表以決定代理程式作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="0799b-118">If you specify schedules from the **Jobs** folder, use the following table to determine the agent job name.</span></span>  
  
|<span data-ttu-id="0799b-119">代理程式</span><span class="sxs-lookup"><span data-stu-id="0799b-119">Agent</span></span>|<span data-ttu-id="0799b-120">作業名稱</span><span class="sxs-lookup"><span data-stu-id="0799b-120">Job name</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="0799b-121">提取訂閱的合併代理程式</span><span class="sxs-lookup"><span data-stu-id="0799b-121">Merge Agent for pull subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|  
|<span data-ttu-id="0799b-122">發送訂閱的合併代理程式</span><span class="sxs-lookup"><span data-stu-id="0799b-122">Merge Agent for push subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
|<span data-ttu-id="0799b-123">發送訂閱的散發代理程式</span><span class="sxs-lookup"><span data-stu-id="0799b-123">Distribution Agent for push subscriptions</span></span>|<span data-ttu-id="0799b-124">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0799b-124">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span></span>|  
|<span data-ttu-id="0799b-125">提取訂閱的散發代理程式</span><span class="sxs-lookup"><span data-stu-id="0799b-125">Distribution Agent for pull subscriptions</span></span>|<span data-ttu-id="0799b-126">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0799b-126">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span></span>|  
|<span data-ttu-id="0799b-127">發送訂閱至非 SQL Server 訂閱者的散發代理程式</span><span class="sxs-lookup"><span data-stu-id="0799b-127">Distribution Agent for push subscriptions to non-SQL Server Subscribers</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
  
 <span data-ttu-id="0799b-128"><sup>1</sup> 要發送訂閱至 Oracle 發行集，其為 \*\*\<Publisher>-\<Publisher**> 而非 **\<Publisher>-\<PublicationDatabase>**</span><span class="sxs-lookup"><span data-stu-id="0799b-128"><sup>1</sup> For push subscriptions to Oracle publications, it is \*\*\<Publisher>-\<Publisher**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
 <span data-ttu-id="0799b-129"><sup>2</sup> 要發送訂閱至 Oracle 發行集，其為 \*\*\<Publisher>-\<DistributionDatabase**> 而非 **\<Publisher>-\<PublicationDatabase>**</span><span class="sxs-lookup"><span data-stu-id="0799b-129"><sup>2</sup> For pull subscriptions to Oracle publications, it is \*\*\<Publisher>-\<DistributionDatabase**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
#### <a name="to-specify-synchronization-schedules"></a><span data-ttu-id="0799b-130">若要指定同步排程</span><span class="sxs-lookup"><span data-stu-id="0799b-130">To specify synchronization schedules</span></span>  
  
1.  <span data-ttu-id="0799b-131">在 [新增訂閱精靈] 的 [同步排程] 頁面，從 [代理程式排程] 下拉式清單中為您正建立的每個訂閱選取下列值的其中之一：</span><span class="sxs-lookup"><span data-stu-id="0799b-131">On the **SynchronizationSchedule** page of the New Subscription Wizard, select one of the following values from the **Agent Schedule** drop-down list for each subscription you are creating:</span></span>  
  
    -   <span data-ttu-id="0799b-132">**連續執行**</span><span class="sxs-lookup"><span data-stu-id="0799b-132">**Run continuously**</span></span>  
  
    -   <span data-ttu-id="0799b-133">**[視需要執行]**</span><span class="sxs-lookup"><span data-stu-id="0799b-133">**Run on demand only**</span></span>  
  
    -   **\<Define Schedule...>**  
  
2.  <span data-ttu-id="0799b-134">如果選取 [\<Define Schedule...>]，請在 [作業排程屬性] 對話方塊中指定排程，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0799b-134">If you select **\<Define Schedule...>**, specify a schedule in the **Job Schedule Properties** dialog box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0799b-135">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="0799b-135">Complete the wizard.</span></span>  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-replication-monitor"></a><span data-ttu-id="0799b-136">若要在「複寫監視器」中修改發送訂閱的同步排程</span><span class="sxs-lookup"><span data-stu-id="0799b-136">To modify a synchronization schedule for a push subscription in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="0799b-137">在複寫監視器的左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="0799b-137">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="0799b-138">按一下 **[所有訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0799b-138">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="0799b-139">以滑鼠右鍵按一下訂閱，然後按一下 **[檢視詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-139">Right-click a subscription, and then click **View Details**.</span></span>  
  
4.  <span data-ttu-id="0799b-140">在 [**訂 \< SubscriptionName> **用帳戶] 視窗中，按一下 [**動作**]，然後按一下 [ \*\* \<AgentName> 作業屬性\*\*]。</span><span class="sxs-lookup"><span data-stu-id="0799b-140">In the **Subscription \< SubscriptionName>** window, click **Action**, and then click **\<AgentName> Job Properties**.</span></span>  
  
5.  <span data-ttu-id="0799b-141">在 [作業屬性 - \<JobName>] 對話方塊的 [排程] 頁面，按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="0799b-141">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
6.  <span data-ttu-id="0799b-142">在 **[作業排程屬性]** 對話方塊中，從 **[排程類型]** 下拉式清單內選取一個值：</span><span class="sxs-lookup"><span data-stu-id="0799b-142">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="0799b-143">若要指定代理程式應持續執行，請選取 **[當 SQL Server Agent 啟動時自動啟動]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-143">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="0799b-144">若要指定代理程式應於排程上執行，請選取 **[重複執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-144">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="0799b-145">若要指定代理程式應視需要執行，請選取 **[執行一次]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-145">To specify that the agent should run on demand, select **One time**.</span></span>  
  
7.  <span data-ttu-id="0799b-146">若您選取 **[重複執行]** ，請為代理程式指定排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-146">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-management-studio"></a><span data-ttu-id="0799b-147">若要在 Management Studio 中修改發送訂閱的同步排程</span><span class="sxs-lookup"><span data-stu-id="0799b-147">To modify a synchronization schedule for a push subscription in Management Studio</span></span>  
  
1.  <span data-ttu-id="0799b-148">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的散發者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="0799b-148">Connect to the Distributor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="0799b-149">展開 **[SQL Server Agent]** 資料夾，然後展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0799b-149">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="0799b-150">以滑鼠右鍵按一下與訂閱相關聯的散發代理程式或合併代理程式的作業，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-150">Right-click the job for the Distribution Agent or Merge Agent associated with the subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0799b-151">在 [作業屬性 - \<JobName>] 對話方塊的 [排程] 頁面，按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="0799b-151">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
5.  <span data-ttu-id="0799b-152">在 **[作業排程屬性]** 對話方塊中，從 **[排程類型]** 下拉式清單內選取一個值：</span><span class="sxs-lookup"><span data-stu-id="0799b-152">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="0799b-153">若要指定代理程式應持續執行，請選取 **[當 SQL Server Agent 啟動時自動啟動]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-153">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="0799b-154">若要指定代理程式應於排程上執行，請選取 **[重複執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-154">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="0799b-155">若要指定代理程式應視需要執行，請選取 **[執行一次]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-155">To specify that the agent should run on demand, select **One time**.</span></span>  
  
6.  <span data-ttu-id="0799b-156">若您選取 **[重複執行]** ，請為代理程式指定排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-156">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-pull-subscription-in-management-studio"></a><span data-ttu-id="0799b-157">若要在 Management Studio 修改提取訂閱的同步排程</span><span class="sxs-lookup"><span data-stu-id="0799b-157">To modify a synchronization schedule for a pull subscription in Management Studio</span></span>  
  
1.  <span data-ttu-id="0799b-158">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="0799b-158">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="0799b-159">展開 **[SQL Server Agent]** 資料夾，然後展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0799b-159">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="0799b-160">以滑鼠右鍵按一下與訂閱相關聯的散發代理程式或合併代理程式的作業，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-160">Right-click the job for the Distribution Agent or Merge Agent associated with the subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0799b-161">在 [作業屬性 - \<JobName>] 對話方塊的 [排程] 頁面，按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="0799b-161">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
5.  <span data-ttu-id="0799b-162">在 **[作業排程屬性]** 對話方塊中，從 **[排程類型]** 下拉式清單內選取一個值：</span><span class="sxs-lookup"><span data-stu-id="0799b-162">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="0799b-163">若要指定代理程式應持續執行，請選取 **[當 SQL Server Agent 啟動時自動啟動]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-163">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="0799b-164">若要指定代理程式應於排程上執行，請選取 **[重複執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-164">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="0799b-165">若要指定代理程式應視需要執行，請選取 **[執行一次]** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-165">To specify that the agent should run on demand, select **One time**.</span></span>  
  
6.  <span data-ttu-id="0799b-166">若您選取 **[重複執行]** ，請為代理程式指定排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-166">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0799b-167">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0799b-167">Using Transact-SQL</span></span>  
 <span data-ttu-id="0799b-168">您可以使用複寫預存程序來以程式設計的方式定義同步排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-168">You can define synchronization schedules programmatically using replication stored procedures.</span></span> <span data-ttu-id="0799b-169">使用哪些預存程序要依複寫的類型和訂閱的類型 (提取訂閱或發送訂閱) 而定。</span><span class="sxs-lookup"><span data-stu-id="0799b-169">The stored procedures that you use depend on the type of replication and the type of subscription (pull or push).</span></span>  
  
 <span data-ttu-id="0799b-170">排程是由下列排程參數所定義，其行為是繼承自 [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)：</span><span class="sxs-lookup"><span data-stu-id="0799b-170">A schedule is defined by the following scheduling parameters, the behaviors of which are inherited from [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql):</span></span>  
  
-   <span data-ttu-id="0799b-171">**@frequency_type**-排程代理程式時所使用的頻率類型。</span><span class="sxs-lookup"><span data-stu-id="0799b-171">**@frequency_type** - the type of frequency used when scheduling the agent.</span></span>  
  
-   <span data-ttu-id="0799b-172">**@frequency_interval**-代理程式執行時的星期幾。</span><span class="sxs-lookup"><span data-stu-id="0799b-172">**@frequency_interval** - the day of the week when an agent runs.</span></span>  
  
-   <span data-ttu-id="0799b-173">**@frequency_relative_interval**-當代理程式排定為要每月執行時，給定月份的周。</span><span class="sxs-lookup"><span data-stu-id="0799b-173">**@frequency_relative_interval** - the week of a given month when the agent is scheduled to run monthly.</span></span>  
  
-   <span data-ttu-id="0799b-174">**@frequency_recurrence_factor**-在同步處理之間發生的頻率類型單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-174">**@frequency_recurrence_factor** - the number of frequency-type units that occur between synchronizations.</span></span>  
  
-   <span data-ttu-id="0799b-175">**@frequency_subday**-代理程式執行頻率超過一天一次以上時的頻率單位。</span><span class="sxs-lookup"><span data-stu-id="0799b-175">**@frequency_subday** - the frequency unit when the agent runs more often than once a day.</span></span>  
  
-   <span data-ttu-id="0799b-176">**@frequency_subday_interval**-代理程式執行頻率超過一天一次以上時，執行之間的頻率單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-176">**@frequency_subday_interval** - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
-   <span data-ttu-id="0799b-177">**@active_start_time_of_day**-代理程式執行時，指定一天中的最早時間會開始。</span><span class="sxs-lookup"><span data-stu-id="0799b-177">**@active_start_time_of_day** - the earliest time in a given day when an agent run will start.</span></span>  
  
-   <span data-ttu-id="0799b-178">**@active_end_time_of_day**-代理程式執行時，指定一天的最晚時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-178">**@active_end_time_of_day** - the latest time in a given day when an agent run will start.</span></span>  
  
-   <span data-ttu-id="0799b-179">**@active_start_date**-代理程式排程生效的第一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-179">**@active_start_date** - the first day that the agent schedule will be in effect.</span></span>  
  
-   <span data-ttu-id="0799b-180">**@active_end_date**-代理程式排程會生效的最後一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-180">**@active_end_date** - the last day that the agent schedule will be in effect.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="0799b-181">針對交易式發行集的提取訂閱定義同步排程</span><span class="sxs-lookup"><span data-stu-id="0799b-181">To define the synchronization schedule for a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="0799b-182">建立交易式發行集的新提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="0799b-182">Create a new pull subscription to a transactional publication.</span></span> <span data-ttu-id="0799b-183">如需詳細資訊，請參閱 [建立提取訂閱](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-183">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="0799b-184">在訂閱者端，執行 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0799b-184">At the Subscriber, execute [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="0799b-185">指定 **@publisher** 、 **@publisher_db** 、 **@publication** ，以及在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 訂閱者端執行散發代理程式的 Windows 認證 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-185">Specify **@publisher**, **@publisher_db**, **@publication**, and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="0799b-186">指定以上詳述的同步處理參數，這些參數會針對同步處理訂閱的散發代理程式作業定義排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-186">Specify the synchronization parameters, detailed above, that define the schedule for the Distribution Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="0799b-187">針對交易式發行集的發送訂閱定義同步排程</span><span class="sxs-lookup"><span data-stu-id="0799b-187">To define the synchronization schedule for a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="0799b-188">建立交易式發行集的新發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="0799b-188">Create a new push subscription to a transactional publication.</span></span> <span data-ttu-id="0799b-189">如需詳細資訊，請參閱 [建立發送訂閱](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-189">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="0799b-190">在訂閱者端，執行 [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0799b-190">At the Subscriber, execute [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="0799b-191">指定 **@subscriber** 、 **@subscriber_db** 、 **@publication** ，以及在訂閱者端執行散發代理程式的 Windows 認證 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-191">Specify **@subscriber**, **@subscriber_db**, **@publication**, and the Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="0799b-192">指定以上詳述的同步處理參數，這些參數會針對同步處理訂閱的散發代理程式作業定義排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-192">Specify the synchronization parameters, detailed above, that define the schedule for the Distribution Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="0799b-193">針對合併式發行集的提取訂閱定義同步排程</span><span class="sxs-lookup"><span data-stu-id="0799b-193">To define the synchronization schedule for a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="0799b-194">建立合併式發行集的新提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="0799b-194">Create a new pull subscription to a merge publication.</span></span> <span data-ttu-id="0799b-195">如需詳細資訊，請參閱 [建立提取訂閱](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-195">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="0799b-196">在訂閱者上，執行 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0799b-196">At the Subscriber, execute [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="0799b-197">指定 **@publisher** 、 **@publisher_db** 、 **@publication** ，以及在訂閱者端執行合併代理程式的 Windows 認證 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-197">Specify **@publisher**, **@publisher_db**, **@publication**, and the Windows credentials under which the Merge Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="0799b-198">指定以上詳述的同步處理參數，這些參數會針對同步處理訂閱的合併代理程式作業定義排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-198">Specify the synchronization parameters, detailed above, that define the schedule for the Merge Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="0799b-199">針對合併式發行集的發送訂閱定義同步排程</span><span class="sxs-lookup"><span data-stu-id="0799b-199">To define the synchronization schedule for a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="0799b-200">建立合併式發行集的新發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="0799b-200">Create a new push subscription to a merge publication.</span></span> <span data-ttu-id="0799b-201">如需詳細資訊，請參閱 [建立發送訂閱](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-201">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="0799b-202">在訂閱者上，執行 [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0799b-202">At the Subscriber, execute [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="0799b-203">指定 **@subscriber** 、 **@subscriber_db** 、 **@publication** ，以及在訂閱者端執行合併代理程式的 Windows 認證 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="0799b-203">Specify **@subscriber**, **@subscriber_db**, **@publication**, and the Windows credentials under which the Merge Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="0799b-204">指定以上詳述的同步處理參數，這些參數會針對同步處理訂閱的合併代理程式作業定義排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-204">Specify the synchronization parameters, detailed above, that define the schedule for the Merge Agent job that synchronizes the subscription.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="0799b-205">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="0799b-205">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="0799b-206">複寫會使用 SQL Server Agent 來排程定期發生之活動的作業，例如快照集的產生和訂閱同步處理。</span><span class="sxs-lookup"><span data-stu-id="0799b-206">Replication uses the SQL Server Agent to schedule jobs for activities that occur periodically, such as snapshot generation and subscription synchronization.</span></span> <span data-ttu-id="0799b-207">您可以使用Replication Management Objects (RMO)，以程式設計方式指定複寫代理程式作業的排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-207">You can use Replication Management Objects (RMO) programmatically to specify schedules for replication agent jobs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0799b-208">當您建立訂閱，並針對 `false` (提取訂閱的預設行為) 指定 `CreateSyncAgentByDefault` 的值時，不會建立代理程式作業，而且會忽略排程屬性。</span><span class="sxs-lookup"><span data-stu-id="0799b-208">When you create a subscription and specify a value `false` for `CreateSyncAgentByDefault` (the default behavior for pull subscriptions) the agent job is not created and scheduling properties are ignored.</span></span> <span data-ttu-id="0799b-209">在此情況下，同步排程必須由應用程式來決定。</span><span class="sxs-lookup"><span data-stu-id="0799b-209">In this case, the synchronization schedule must be determined by the application.</span></span> <span data-ttu-id="0799b-210">如需相關資訊，請參閱 [Create a Pull Subscription](create-a-pull-subscription.md) 及 [Create a Push Subscription](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-210">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md) and [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="0799b-211">當您建立交易式發行集的發送訂閱時，定義複寫代理程式排程</span><span class="sxs-lookup"><span data-stu-id="0799b-211">To define a replication agent schedule when you create a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="0799b-212">為您所建立的訂閱建立 <xref:Microsoft.SqlServer.Replication.TransSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0799b-212">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="0799b-213">如需詳細資訊，請參閱 [建立發送訂閱](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-213">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="0799b-214">在您呼叫 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>之前，請設定 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> 屬性的下列一或多個欄位：</span><span class="sxs-lookup"><span data-stu-id="0799b-214">Before you call <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="0799b-215"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 當您排程代理程式時，所用的頻率類型 (如每天或每週)。</span><span class="sxs-lookup"><span data-stu-id="0799b-215"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="0799b-216"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 代理程式執行之一週中的日子。</span><span class="sxs-lookup"><span data-stu-id="0799b-216"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="0799b-217"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 當代理程式排定為要每月執行時，給定月份的週。</span><span class="sxs-lookup"><span data-stu-id="0799b-217"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month when the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="0799b-218"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 在同步處理之間發生的頻率類型單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-218"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="0799b-219"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 代理程式執行頻率超過一天一次以上時的頻率單位。</span><span class="sxs-lookup"><span data-stu-id="0799b-219"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="0799b-220"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 代理程式執行頻率超過一天一次以上時，執行之間的頻率單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-220"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="0799b-221"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 代理程式在給定日子開始執行的最早時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-221"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="0799b-222"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 代理程式在給定日子開始執行的最晚時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-222"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="0799b-223"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 代理程式排程生效的第一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-223"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="0799b-224"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 代理程式排程有效的最後一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-224"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0799b-225">若未指定這些屬性的其中一個，則會設定預設值。</span><span class="sxs-lookup"><span data-stu-id="0799b-225">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="0799b-226">呼叫 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 方法來建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="0799b-226">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="0799b-227">當您建立交易式發行集的提取訂閱時，定義複寫代理程式排程</span><span class="sxs-lookup"><span data-stu-id="0799b-227">To define a replication agent schedule when you create a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="0799b-228">為您所建立的訂閱建立 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0799b-228">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="0799b-229">如需詳細資訊，請參閱 [建立提取訂閱](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-229">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="0799b-230">在您呼叫 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>之前，請設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> 屬性的下列一或多個欄位：</span><span class="sxs-lookup"><span data-stu-id="0799b-230">Before you call <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="0799b-231"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 當您排程代理程式時，所用的頻率類型 (如每天或每週)。</span><span class="sxs-lookup"><span data-stu-id="0799b-231"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="0799b-232"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 代理程式執行之一週中的日子。</span><span class="sxs-lookup"><span data-stu-id="0799b-232"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="0799b-233"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 當代理程式排定為要每月執行時，給定月份的週。</span><span class="sxs-lookup"><span data-stu-id="0799b-233"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="0799b-234"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 在同步處理之間發生的頻率類型單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-234"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="0799b-235"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 代理程式執行頻率超過一天一次以上時的頻率單位。</span><span class="sxs-lookup"><span data-stu-id="0799b-235"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="0799b-236"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 代理程式執行頻率超過一天一次以上時，執行之間的頻率單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-236"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="0799b-237"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 代理程式在給定日子開始執行的最早時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-237"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="0799b-238"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 代理程式在給定日子開始執行的最晚時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-238"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="0799b-239"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 代理程式排程生效的第一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-239"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="0799b-240"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 代理程式排程有效的最後一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-240"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0799b-241">若未指定這些屬性的其中一個，則會設定預設值。</span><span class="sxs-lookup"><span data-stu-id="0799b-241">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="0799b-242">呼叫 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> 方法來建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="0799b-242">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="0799b-243">當您建立合併式發行集的提取訂閱時，定義複寫代理程式排程</span><span class="sxs-lookup"><span data-stu-id="0799b-243">To define a replication agent schedule when you create a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="0799b-244">為您所建立的訂閱建立 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0799b-244">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="0799b-245">如需詳細資訊，請參閱 [建立提取訂閱](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-245">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="0799b-246">在您呼叫 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>之前，請設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> 屬性的下列一或多個欄位：</span><span class="sxs-lookup"><span data-stu-id="0799b-246">Before you call <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="0799b-247"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 當您排程代理程式時，所用的頻率類型 (如每天或每週)。</span><span class="sxs-lookup"><span data-stu-id="0799b-247"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="0799b-248"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 代理程式執行之一週中的日子。</span><span class="sxs-lookup"><span data-stu-id="0799b-248"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="0799b-249"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 當代理程式排定為要每月執行時，給定月份的週。</span><span class="sxs-lookup"><span data-stu-id="0799b-249"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="0799b-250"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 在同步處理之間發生的頻率類型單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-250"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="0799b-251"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 代理程式執行頻率超過一天一次以上時的頻率單位。</span><span class="sxs-lookup"><span data-stu-id="0799b-251"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="0799b-252"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 代理程式執行頻率超過一天一次以上時，執行之間的頻率單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-252"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="0799b-253"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 代理程式在給定日子開始執行的最早時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-253"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="0799b-254"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 代理程式在給定日子開始執行的最晚時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-254"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="0799b-255"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 代理程式排程生效的第一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-255"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="0799b-256"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 代理程式排程有效的最後一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-256"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0799b-257">若未指定這些屬性的其中一個，則會設定預設值。</span><span class="sxs-lookup"><span data-stu-id="0799b-257">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="0799b-258">呼叫 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> 方法來建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="0799b-258">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="0799b-259">當您建立合併式發行集的發送訂閱時，定義複寫代理程式排程</span><span class="sxs-lookup"><span data-stu-id="0799b-259">To define a replication agent schedule when you create a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="0799b-260">為您所建立的訂閱建立 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0799b-260">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="0799b-261">如需詳細資訊，請參閱 [建立發送訂閱](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="0799b-261">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="0799b-262">在您呼叫 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>之前，請設定 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> 屬性的下列一或多個欄位：</span><span class="sxs-lookup"><span data-stu-id="0799b-262">Before you call <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="0799b-263"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 當您排程代理程式時，所用的頻率類型 (如每天或每週)。</span><span class="sxs-lookup"><span data-stu-id="0799b-263"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="0799b-264"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 代理程式執行之一週中的日子。</span><span class="sxs-lookup"><span data-stu-id="0799b-264"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="0799b-265"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 當代理程式排定為要每月執行時，給定月份的週。</span><span class="sxs-lookup"><span data-stu-id="0799b-265"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="0799b-266"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 在同步處理之間發生的頻率類型單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-266"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="0799b-267"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 代理程式執行頻率超過一天一次以上時的頻率單位。</span><span class="sxs-lookup"><span data-stu-id="0799b-267"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="0799b-268"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 代理程式執行頻率超過一天一次以上時，執行之間的頻率單位數目。</span><span class="sxs-lookup"><span data-stu-id="0799b-268"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="0799b-269"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 代理程式在給定日子開始執行的最早時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-269"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="0799b-270"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 代理程式在給定日子開始執行的最晚時間。</span><span class="sxs-lookup"><span data-stu-id="0799b-270"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="0799b-271"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 代理程式排程生效的第一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-271"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="0799b-272"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 代理程式排程有效的最後一天。</span><span class="sxs-lookup"><span data-stu-id="0799b-272"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0799b-273">若未指定這些屬性的其中一個，則會設定預設值。</span><span class="sxs-lookup"><span data-stu-id="0799b-273">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="0799b-274">呼叫 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 方法來建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="0799b-274">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> method to create the subscription.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="0799b-275">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="0799b-275">Example (RMO)</span></span>  
 <span data-ttu-id="0799b-276">此範例會建立合併式發行集的發送訂閱，並指定同步處理此訂閱所依據的排程。</span><span class="sxs-lookup"><span data-stu-id="0799b-276">This example creates a push subscription to a merge publication and specifies the schedule on which the subscription is synchronized.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="0799b-277">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0799b-277">See Also</span></span>  
 <span data-ttu-id="0799b-278">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="0799b-278">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="0799b-279">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="0799b-279">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="0799b-280">[同步處理發送訂閱](synchronize-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="0799b-280">[Synchronize a Push Subscription](synchronize-a-push-subscription.md) </span></span>  
 <span data-ttu-id="0799b-281">[同步處理提取訂閱](synchronize-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="0799b-281">[Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="0799b-282">同步處理資料</span><span class="sxs-lookup"><span data-stu-id="0799b-282">Synchronize Data</span></span>](synchronize-data.md)  
  
  
