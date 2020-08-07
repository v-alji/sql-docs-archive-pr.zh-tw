---
title: 同步處理提取訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], synchronizing
- synchronization [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
ms.assetid: 3ca24b23-fdc3-408e-8208-a2ace48fc8e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 826622cd17862c0535e60c01baab756af2b2996b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596648"
---
# <a name="synchronize-a-pull-subscription"></a><span data-ttu-id="d7381-102">同步處理提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d7381-102">Synchronize a Pull Subscription</span></span>
  <span data-ttu-id="d7381-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]複寫代理程式 [或 Replication Management Objects (RMO) 來同步處理](agents/replication-agents-overview.md)中的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d7381-103">This topic describes how to synchronize a pull subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [replication agents](agents/replication-agents-overview.md), or Replication Management Objects (RMO).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d7381-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d7381-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d7381-105">訂閱是由散發代理程式 (適用於快照式與異動複寫) 或合併代理程式 (適用於合併式複寫) 同步處理。</span><span class="sxs-lookup"><span data-stu-id="d7381-105">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="d7381-106">代理程式可以繼續執行、視需要執行，或是依照排程執行。</span><span class="sxs-lookup"><span data-stu-id="d7381-106">Agents can run continuously, run on demand, or run on a schedule.</span></span> <span data-ttu-id="d7381-107">如需指定同步處理排程的詳細資訊，請參閱[指定同步處理排程](specify-synchronization-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="d7381-107">For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="d7381-108">從 **中的** [本機訂閱] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]資料夾視需要同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="d7381-108">Synchronize a subscription on demand from the **Local Subscriptions** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-on-demand-in-management-studio"></a><span data-ttu-id="d7381-109">若要在 Management Studio 中視需要同步處理提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d7381-109">To synchronize a pull subscription on demand in Management Studio</span></span>  
  
1.  <span data-ttu-id="d7381-110">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="d7381-110">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="d7381-111">展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d7381-111">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="d7381-112">以滑鼠右鍵按一下您要同步處理的訂閱，然後按一下 **[檢視同步處理的狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="d7381-112">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="d7381-113">在 [檢視同步處理的狀態 - \<Subscriber>\<SubscriptionDatabase>] 對話方塊中，按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="d7381-113">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="d7381-114">同步處理完成後，會顯示 **[同步處理已完成]** 的訊息。</span><span class="sxs-lookup"><span data-stu-id="d7381-114">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
5.  <span data-ttu-id="d7381-115">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="d7381-115">Click **Close**.</span></span>  
  
##  <a name="replication-agents"></a><a name="ReplProg"></a> <span data-ttu-id="d7381-116">Replication Agents</span><span class="sxs-lookup"><span data-stu-id="d7381-116">Replication Agents</span></span>  
 <span data-ttu-id="d7381-117">提取訂閱可透過程式設計方式加以同步處理，以及視需要從命令提示字元叫用適當的複寫代理程式可執行檔加以同步處理。</span><span class="sxs-lookup"><span data-stu-id="d7381-117">Pull subscriptions can be synchronized programmatically and on-demand by invoking the appropriate replication agent executable file from the command prompt.</span></span> <span data-ttu-id="d7381-118">叫用的複寫代理程式可執行檔取決於提取訂閱所屬的發行集類型。</span><span class="sxs-lookup"><span data-stu-id="d7381-118">The replication agent executable file that is invoked will depend on the type of publication to which the pull subscription belongs.</span></span> <span data-ttu-id="d7381-119">如需詳細資訊，請參閱 [Replication Agents](agents/replication-agents-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d7381-119">For more information, see [Replication Agents](agents/replication-agents-overview.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7381-120">複寫代理程式會使用從命令提示字元啟動此代理程式之使用者的 Windows 驗證認證，連接到本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="d7381-120">Replication agents connect to the local server using the Windows Authentication credentials of the user who started the agent from the command prompt.</span></span> <span data-ttu-id="d7381-121">當使用「Windows 整合式驗證」連接到遠端伺服器時，也會使用這些 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="d7381-121">These Windows credentials are also used when connecting to remote servers using Windows Integrated Authentication.</span></span>  
  
#### <a name="to-start-the-distribution-agent-from-the-command-prompt-or-from-a-batch-file"></a><span data-ttu-id="d7381-122">從命令提示字元或批次檔執行散發代理程式</span><span class="sxs-lookup"><span data-stu-id="d7381-122">To start the distribution agent from the command prompt or from a batch file</span></span>  
  
1.  <span data-ttu-id="d7381-123">從命令提示字元或批次檔中，執行 [distrib.exe](agents/replication-distribution-agent.md) 來啟動 **複寫散發代理程式**，並指定下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="d7381-123">From the command prompt or in a batch file, start the [Replication Distribution Agent](agents/replication-distribution-agent.md) by running **distrib.exe**, specifying the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="d7381-124">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="d7381-124">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="d7381-125">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="d7381-125">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="d7381-126">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="d7381-126">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="d7381-127">**-DistributorSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="d7381-127">**-DistributorSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="d7381-128">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="d7381-128">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="d7381-129">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="d7381-129">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="d7381-130">**-SubscriberSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="d7381-130">**-SubscriberSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="d7381-131">**-SubscriptionType** = **1**</span><span class="sxs-lookup"><span data-stu-id="d7381-131">**-SubscriptionType** = **1**</span></span>  
  
     <span data-ttu-id="d7381-132">如果您正在使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證」，您也必須指定下列引數：</span><span class="sxs-lookup"><span data-stu-id="d7381-132">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="d7381-133">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="d7381-133">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="d7381-134">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="d7381-134">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="d7381-135">**-DistributorSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="d7381-135">**-DistributorSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="d7381-136">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="d7381-136">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="d7381-137">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="d7381-137">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="d7381-138">**-PublisherSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="d7381-138">**-PublisherSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="d7381-139">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="d7381-139">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="d7381-140">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="d7381-140">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="d7381-141">**-SubscriberSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="d7381-141">**-SubscriberSecurityMode** = **0**</span></span>  
  
#### <a name="to-start-the-merge-agent-from-the-command-prompt-or-from-a-batch-file"></a><span data-ttu-id="d7381-142">從命令提示字元或批次檔執行合併代理程式</span><span class="sxs-lookup"><span data-stu-id="d7381-142">To start the merge agent from the command prompt or from a batch file</span></span>  
  
1.  <span data-ttu-id="d7381-143">從命令提示字元或批次檔中，執行 [replmerg.exe](agents/replication-merge-agent.md) 來啟動 **複寫合併代理程式**，並指定下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="d7381-143">From the command prompt or in a batch file, start the [Replication Merge Agent](agents/replication-merge-agent.md) by running **replmerg.exe**, specifying the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="d7381-144">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="d7381-144">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="d7381-145">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="d7381-145">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="d7381-146">**-PublisherSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="d7381-146">**-PublisherSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="d7381-147">**-Publication**</span><span class="sxs-lookup"><span data-stu-id="d7381-147">**-Publication**</span></span>  
  
    -   <span data-ttu-id="d7381-148">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="d7381-148">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="d7381-149">**-DistributorSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="d7381-149">**-DistributorSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="d7381-150">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="d7381-150">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="d7381-151">**-SubscriberSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="d7381-151">**-SubscriberSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="d7381-152">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="d7381-152">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="d7381-153">**-SubscriptionType** = **1**</span><span class="sxs-lookup"><span data-stu-id="d7381-153">**-SubscriptionType** = **1**</span></span>  
  
     <span data-ttu-id="d7381-154">如果您正在使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證」，您也必須指定下列引數：</span><span class="sxs-lookup"><span data-stu-id="d7381-154">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="d7381-155">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="d7381-155">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="d7381-156">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="d7381-156">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="d7381-157">**-DistributorSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="d7381-157">**-DistributorSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="d7381-158">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="d7381-158">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="d7381-159">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="d7381-159">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="d7381-160">**-PublisherSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="d7381-160">**-PublisherSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="d7381-161">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="d7381-161">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="d7381-162">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="d7381-162">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="d7381-163">**-SubscriberSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="d7381-163">**-SubscriberSecurityMode** = **0**</span></span>  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> <span data-ttu-id="d7381-164">範例 (複寫代理程式)</span><span class="sxs-lookup"><span data-stu-id="d7381-164">Examples (Replication Agents)</span></span>  
 <span data-ttu-id="d7381-165">下列範例會啟動散發代理程式，以同步處理提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d7381-165">The following example starts the Distribution Agent to synchronize a pull subscription.</span></span> <span data-ttu-id="d7381-166">所有的連接都是使用「Windows 驗證」所建立。</span><span class="sxs-lookup"><span data-stu-id="d7381-166">All connections are made using Windows Authentication.</span></span>  
  
 [!code-sql[HowTo#bat_synctranpullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/synctranpullsub_10.bat)]  
  
 <span data-ttu-id="d7381-167">下列範例會啟動合併代理程式，以同步處理提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d7381-167">The following example starts the Merge Agent to synchronize a pull subscription.</span></span> <span data-ttu-id="d7381-168">所有的連接都是使用「Windows 驗證」所建立。</span><span class="sxs-lookup"><span data-stu-id="d7381-168">All connections are made using Windows Authentication.</span></span>  
  
 [!code-sql[HowTo#bat_syncmergepullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/syncmergepullsub_10.bat)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="d7381-169">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="d7381-169">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="d7381-170">您可以使用 Replication Management Objects (RMO) 和對複寫代理程式功能的 Managed 程式碼存取，以程式設計的方式同步處理提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d7381-170">You can synchronize pull subscriptions programmatically by using Replication Management Objects (RMO) and managed code access to replication agent functionalities.</span></span> <span data-ttu-id="d7381-171">用於同步處理提取訂閱的類別依該訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="d7381-171">The classes you use to synchronize a pull subscription depend on the type of publication to which the subscription belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7381-172">如果您要啟動自發執行的同步處理而不影響應用程式，請非同步啟動代理程式。</span><span class="sxs-lookup"><span data-stu-id="d7381-172">If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously.</span></span> <span data-ttu-id="d7381-173">不過，如果要監視同步處理的結果並在同步處理期間從代理程式接收回撥 (例如，顯示進度列)，您就應該同步啟動代理程式。</span><span class="sxs-lookup"><span data-stu-id="d7381-173">However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process (for example, to display a progress bar), you should start the agent synchronously.</span></span> <span data-ttu-id="d7381-174">對於 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 訂閱者，您必須同步啟動代理程式。</span><span class="sxs-lookup"><span data-stu-id="d7381-174">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers, you must start the agent synchronously.</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="d7381-175">若要同步處理快照式或交易式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d7381-175">To synchronize a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="d7381-176">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="d7381-176">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="d7381-177">建立 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 類別的執行個體，並設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d7381-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="d7381-178">將 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>設為訂閱資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="d7381-178">The subscription database name for <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="d7381-179">將 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>設為訂閱所屬發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7381-179">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="d7381-180">將 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>設定為發行集資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="d7381-180">The name of the publication database for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="d7381-181">將 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>設為「發行者」的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7381-181">The name of the Publisher for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.</span></span>  
  
    -   <span data-ttu-id="d7381-182">將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>設為步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="d7381-182">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="d7381-183">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得剩餘的訂閱屬性。</span><span class="sxs-lookup"><span data-stu-id="d7381-183">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="d7381-184">如果此方法傳回 `false`，請確認該訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="d7381-184">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="d7381-185">以下列其中一種方式啟動「訂閱者」上的「散發代理程式」：</span><span class="sxs-lookup"><span data-stu-id="d7381-185">Start the Distribution Agent at the Subscriber in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="d7381-186">從步驟 2 的 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> 執行個體上呼叫 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 方法。</span><span class="sxs-lookup"><span data-stu-id="d7381-186">Call the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.TransPullSubscription> from step 2.</span></span> <span data-ttu-id="d7381-187">此方法會以非同步方式啟動散發代理程式，並且控制項會在代理程式作業執行時立即傳回至應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7381-187">This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="d7381-188">您不可以針對「[!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 訂閱者」呼叫此方法，或者如果訂閱是以 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> 的 `false` 值 (預設值) 建立的，也不可以。</span><span class="sxs-lookup"><span data-stu-id="d7381-188">You cannot call this method for [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers or if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default).</span></span>  
  
    -   <span data-ttu-id="d7381-189">從 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> 屬性取得 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> 類別的執行個體，並呼叫 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d7381-189">Get an instance of the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="d7381-190">此方法會同步啟動代理程式，而控制項仍會停留於正在執行的代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="d7381-190">This method starts the agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="d7381-191">在同步執行期間，您可以在代理程式執行時處理 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> 事件。</span><span class="sxs-lookup"><span data-stu-id="d7381-191">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d7381-192">如果您在 `false` <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> 建立提取訂閱時，將的值指定為 (預設) ，則也需要指定、和（選擇性）， <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A> 因為在 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)中無法使用訂閱的代理程式作業相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d7381-192">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default) when you created the pull subscription, you also need to specify <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A>, and optionally <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> and <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> because the agent job related metadata for the subscription is not available in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="d7381-193">若要同步處理合併式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d7381-193">To synchronize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="d7381-194">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="d7381-194">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="d7381-195">建立 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 類別的執行個體，並設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d7381-195">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="d7381-196">將 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>設為訂閱資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="d7381-196">The subscription database name for <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="d7381-197">將 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>設為訂閱所屬發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7381-197">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="d7381-198">將 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>設為發行的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="d7381-198">The name of the published database for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="d7381-199">將 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>設為「發行者」的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7381-199">The name of the Publisher for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.</span></span>  
  
    -   <span data-ttu-id="d7381-200">將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>設為步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="d7381-200">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="d7381-201">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得剩餘的訂閱屬性。</span><span class="sxs-lookup"><span data-stu-id="d7381-201">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="d7381-202">如果此方法傳回 `false`，請確認該訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="d7381-202">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="d7381-203">以下列其中一種方式啟動「訂閱者」上的「合併代理程式」：</span><span class="sxs-lookup"><span data-stu-id="d7381-203">Start the Merge Agent at the Subscriber in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="d7381-204">從步驟 2 的 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> 執行個體上呼叫 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 方法。</span><span class="sxs-lookup"><span data-stu-id="d7381-204">Call the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.MergePullSubscription> from step 2.</span></span> <span data-ttu-id="d7381-205">此方法會以非同步方式啟動合併代理程式，並且控制項會在代理程式作業執行時立即傳回至應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7381-205">This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="d7381-206">您不可以針對「[!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 訂閱者」呼叫此方法，或者如果訂閱是以 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> 的 `false` 值 (預設值) 建立的，也不可以。</span><span class="sxs-lookup"><span data-stu-id="d7381-206">You cannot call this method for [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers or if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default).</span></span>  
  
    -   <span data-ttu-id="d7381-207">從 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> 屬性取得 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> 類別的執行個體，並呼叫 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d7381-207">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="d7381-208">此方法會同步啟動「合併代理程式」，而控制項仍會停留於正在執行的代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="d7381-208">This method starts the Merge Agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="d7381-209">在同步執行期間，您可以在代理程式執行時處理 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> 事件。</span><span class="sxs-lookup"><span data-stu-id="d7381-209">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d7381-210">如果您在 `false` <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> 建立提取訂閱時，將的值指定為 (預設) ，則也需要指定 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A> 、 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A> 、、、、和（選擇性）、、和， <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A> 因為在 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)中無法使用訂閱的代理程式作業相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d7381-210">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default) when you created the pull subscription, you also need to specify <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A>, and optionally <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A>, and <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> because the agent job related metadata for the subscription is not available in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="d7381-211">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="d7381-211">Examples (RMO)</span></span>  
 <span data-ttu-id="d7381-212">此範例同步處理交易式發行集的提取訂閱，其中代理程式會使用代理程式作業非同步啟動。</span><span class="sxs-lookup"><span data-stu-id="d7381-212">This example synchronizes a pull subscription to a transactional publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub_withjob)]  
  
 <span data-ttu-id="d7381-213">此範例同步處理交易式發行集的提取訂閱，其中代理程式會同步啟動。</span><span class="sxs-lookup"><span data-stu-id="d7381-213">This example synchronizes a pull subscription to a transactional publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub)]  
  
 <span data-ttu-id="d7381-214">此範例同步處理合併式發行集的提取訂閱，其中代理程式會使用代理程式作業非同步啟動。</span><span class="sxs-lookup"><span data-stu-id="d7381-214">This example synchronizes a pull subscription to a merge publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_withjob)]  
  
 <span data-ttu-id="d7381-215">此範例同步處理合併式發行集的提取訂閱，其中代理程式會同步啟動。</span><span class="sxs-lookup"><span data-stu-id="d7381-215">This example synchronizes a pull subscription to a merge publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub)]  
  
 <span data-ttu-id="d7381-216">此範例使用 Web 同步處理來同步處理合併式發行集的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d7381-216">This example synchronizes a pull subscription to a merge publication using Web synchronization.</span></span> <span data-ttu-id="d7381-217">該訂閱是在沒有代理程式作業和相關訂閱中繼資料的情況下建立的，因此必須同步啟動代理程式並提供其他訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="d7381-217">The subscription was created without the agent job and related subscription metadata, so the agent must be started synchronously and additional subscription information is supplied.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_NoJobWebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_nojobwebsync)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_NoJobWebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_nojobwebsync)]  
  
## <a name="see-also"></a><span data-ttu-id="d7381-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7381-218">See Also</span></span>  
 <span data-ttu-id="d7381-219">[同步處理資料](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="d7381-219">[Synchronize Data](synchronize-data.md) </span></span>  
 <span data-ttu-id="d7381-220">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="d7381-220">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="d7381-221">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="d7381-221">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
