---
title: 同步處理發送訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], push subscriptions
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], synchronizing
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fb2f7bd961748272d6cd67e3412b09d9370a6f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701026"
---
# <a name="synchronize-a-push-subscription"></a><span data-ttu-id="1c1ec-102">同步處理發送訂閱</span><span class="sxs-lookup"><span data-stu-id="1c1ec-102">Synchronize a Push Subscription</span></span>
  <span data-ttu-id="1c1ec-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]複寫代理程式 [或 Replication Management Objects (RMO) 來同步處理](agents/replication-agents-overview.md)中的發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-103">This topic describes how to synchronize a push subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [replication agents](agents/replication-agents-overview.md), or Replication Management Objects (RMO).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1c1ec-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c1ec-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1c1ec-105">訂閱是由散發代理程式 (適用於快照式與異動複寫) 或合併代理程式 (適用於合併式複寫) 同步處理。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-105">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="1c1ec-106">代理程式可以繼續執行、視需要執行，或是依照排程執行。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-106">Agents can run continuously, run on demand, or run on a schedule.</span></span> <span data-ttu-id="1c1ec-107">如需指定同步處理排程的詳細資訊，請參閱[指定同步處理排程](specify-synchronization-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-107">For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="1c1ec-108">需要時從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [本機發行集] 和 [本機訂閱] 資料夾，以及複寫監視器中的 [所有訂閱] 索引標籤同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-108">Synchronize a subscription on demand from the **Local Publications** and **Local Subscriptions** folders in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and the **All Subscriptions** tab in Replication Monitor.</span></span> <span data-ttu-id="1c1ec-109">Oracle 發行集的訂閱無法在需要時從「訂閱者」同步處理。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-109">Subscriptions to Oracle publications cannot be synchronized on demand from the Subscriber.</span></span> <span data-ttu-id="1c1ec-110">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-110">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-publisher"></a><span data-ttu-id="1c1ec-111">需要時在 Management Studio 上同步處理發送訂閱 (發行者端)</span><span class="sxs-lookup"><span data-stu-id="1c1ec-111">To synchronize a push subscription on demand in Management Studio (at the Publisher)</span></span>  
  
1.  <span data-ttu-id="1c1ec-112">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-112">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="1c1ec-113">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-113">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="1c1ec-114">展開您要同步處理其訂閱的發行集。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-114">Expand the publication for which you want to synchronize subscriptions.</span></span>  
  
4.  <span data-ttu-id="1c1ec-115">以滑鼠右鍵按一下您要同步處理的訂閱，然後按一下 **[檢視同步處理的狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-115">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
5.  <span data-ttu-id="1c1ec-116">在 [檢視同步處理的狀態 - \<Subscriber>\<SubscriptionDatabase>] 對話方塊中，按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-116">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="1c1ec-117">同步處理完成後，會顯示 **[同步處理已完成]** 的訊息。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-117">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
6.  <span data-ttu-id="1c1ec-118">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-118">Click **Close**.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-subscriber"></a><span data-ttu-id="1c1ec-119">需要時在 Management Studio 上同步處理發送訂閱 (訂閱者端)</span><span class="sxs-lookup"><span data-stu-id="1c1ec-119">To synchronize a push subscription on demand in Management Studio (at the Subscriber)</span></span>  
  
1.  <span data-ttu-id="1c1ec-120">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-120">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="1c1ec-121">展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="1c1ec-122">以滑鼠右鍵按一下您要同步處理的訂閱，然後按一下 **[檢視同步處理的狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-122">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="1c1ec-123">接著會顯示有關建立連接到「散發者」的訊息。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-123">A message is displayed about establishing a connection to the Distributor.</span></span> <span data-ttu-id="1c1ec-124">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-124">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1c1ec-125">在 [檢視同步處理的狀態 - \<Subscriber>:\<SubscriptionDatabase>] 對話方塊中，按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-125">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="1c1ec-126">同步處理完成後，會顯示 **[同步處理已完成]** 的訊息。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-126">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
6.  <span data-ttu-id="1c1ec-127">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-127">Click **Close**.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-replication-monitor"></a><span data-ttu-id="1c1ec-128">需要時在複寫監視器中同步處理發送訂閱</span><span class="sxs-lookup"><span data-stu-id="1c1ec-128">To synchronize a push subscription on demand in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="1c1ec-129">在複寫監視器中，展開左窗格裡的發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-129">In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="1c1ec-130">按一下 **[所有訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-130">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="1c1ec-131">以滑鼠右鍵按一下您要同步處理的訂閱，再按一下 **[啟動同步處理]** 。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-131">Right-click the subscription you want to synchronize, and then click **Start Synchronizing**.</span></span>  
  
4.  <span data-ttu-id="1c1ec-132">若要檢視同步處理的進度，以滑鼠右鍵按一下該訂閱，再按一下 **[檢視詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-132">To view synchronization progress, right-click the subscription, and then click **View Details**.</span></span>  
  
##  <a name="using-replication-agents"></a><a name="ReplProg"></a> <span data-ttu-id="1c1ec-133">使用複寫代理程式</span><span class="sxs-lookup"><span data-stu-id="1c1ec-133">Using Replication Agents</span></span>  
 <span data-ttu-id="1c1ec-134">發送訂閱可透過程式設計方式加以同步處理，以及視需要從命令提示字元叫用適當的複寫代理程式可執行檔加以同步處理。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-134">Push subscriptions can be synchronized programmatically and on-demand by invoking the appropriate replication agent executable file from the command prompt.</span></span> <span data-ttu-id="1c1ec-135">叫用的複寫代理程式可執行檔取決於發送訂閱所屬的發行集類型。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-135">The replication agent executable file that is invoked will depend on the type of publication to which the push subscription belongs.</span></span>  
  
#### <a name="to-start-the-distribution-agent-to-synchronize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="1c1ec-136">啟動散發代理程式，以同步處理交易式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="1c1ec-136">To start the Distribution Agent to synchronize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="1c1ec-137">從命令提示字元或是散發者上的批次檔中，執行 **distrib.exe**。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-137">From the command prompt or in a batch file at the Distributor, execute **distrib.exe**.</span></span> <span data-ttu-id="1c1ec-138">指定下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="1c1ec-138">Specify the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="1c1ec-139">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-139">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="1c1ec-140">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-140">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="1c1ec-141">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-141">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="1c1ec-142">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-142">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="1c1ec-143">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-143">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="1c1ec-144">**-SubscriptionType = 0**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-144">**-SubscriptionType = 0**</span></span>  
  
     <span data-ttu-id="1c1ec-145">無果您正在使用「SQL Server 驗證」，您也必須指定下列引數：</span><span class="sxs-lookup"><span data-stu-id="1c1ec-145">If you are using SQL Server Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="1c1ec-146">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-146">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="1c1ec-147">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-147">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="1c1ec-148">**-DistributorSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-148">**-DistributorSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="1c1ec-149">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-149">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="1c1ec-150">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-150">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="1c1ec-151">**-PublisherSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-151">**-PublisherSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="1c1ec-152">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-152">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="1c1ec-153">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-153">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="1c1ec-154">**-SubscriberSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-154">**-SubscriberSecurityMode = 0**</span></span>  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
#### <a name="to-start-the-merge-agent-to-synchronize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="1c1ec-155">啟動合併代理程式，以同步處理合併式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="1c1ec-155">To start the Merge Agent to synchronize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="1c1ec-156">從命令提示字元或是散發者上的批次檔中，執行 **replmerg.exe**。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-156">From the command prompt or in a batch file at the Distributor, execute **replmerg.exe**.</span></span> <span data-ttu-id="1c1ec-157">指定下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="1c1ec-157">Specify the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="1c1ec-158">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-158">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="1c1ec-159">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-159">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="1c1ec-160">**-Publication**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-160">**-Publication**</span></span>  
  
    -   <span data-ttu-id="1c1ec-161">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-161">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="1c1ec-162">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-162">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="1c1ec-163">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-163">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="1c1ec-164">**-SubscriptionType = 0**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-164">**-SubscriptionType = 0**</span></span>  
  
     <span data-ttu-id="1c1ec-165">無果您正在使用「SQL Server 驗證」，您也必須指定下列引數：</span><span class="sxs-lookup"><span data-stu-id="1c1ec-165">If you are using SQL Server Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="1c1ec-166">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-166">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="1c1ec-167">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-167">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="1c1ec-168">**-DistributorSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-168">**-DistributorSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="1c1ec-169">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-169">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="1c1ec-170">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-170">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="1c1ec-171">**-PublisherSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-171">**-PublisherSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="1c1ec-172">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-172">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="1c1ec-173">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-173">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="1c1ec-174">**-SubscriberSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="1c1ec-174">**-SubscriberSecurityMode = 0**</span></span>  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> <span data-ttu-id="1c1ec-175">範例 (複寫代理程式)</span><span class="sxs-lookup"><span data-stu-id="1c1ec-175">Examples (Replication Agents)</span></span>  
 <span data-ttu-id="1c1ec-176">下列範例會啟動散發代理程式，以同步處理發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-176">The following example starts the Distribution Agent to synchronize a push subscription.</span></span>  
  
 
```
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4
```
  
 <span data-ttu-id="1c1ec-177">下列範例會啟動合併代理程式，以同步處理發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-177">The following example starts the Merge Agent to synchronize a push subscription.</span></span>  

```
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1
```
  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="1c1ec-178">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="1c1ec-178">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="1c1ec-179">您可以使用 Replication Management Objects (RMO) 和對複寫代理程式功能的 Managed 程式碼存取，以程式設計的方式同步處理發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-179">You can synchronize push subscriptions programmatically by using Replication Management Objects (RMO) and managed code access to replication agent functionalities.</span></span> <span data-ttu-id="1c1ec-180">用於同步處理發送訂閱的類別依該訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-180">The classes that you use to synchronize a push subscription depend on the type of publication to which the subscription belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c1ec-181">如果您要啟動自發執行的同步處理而不影響應用程式，請非同步啟動代理程式。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-181">If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously.</span></span> <span data-ttu-id="1c1ec-182">不過，如果要監視同步處理的結果並在同步處理期間從代理程式接收回撥 (例如，如果要顯示進度列)，您就應該同步啟動代理程式。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-182">However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process (for example, if you want to display a progress bar), you should start the agent synchronously.</span></span> <span data-ttu-id="1c1ec-183">對於 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 訂閱者，您必須同步啟動代理程式。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-183">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers, you must start the agent synchronously.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="1c1ec-184">若要同步處理快照式或交易式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="1c1ec-184">To synchronize a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="1c1ec-185">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-185">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1c1ec-186">建立 <xref:Microsoft.SqlServer.Replication.TransSubscription> 類別的執行個體，並設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="1c1ec-186">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class and set the following properties:</span></span>  
  
    -   <span data-ttu-id="1c1ec-187">將 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>設為發行集資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-187">The publication database name for <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-188">將 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>設為訂閱所屬發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-188">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-189">將 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>設為訂閱資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-189">The name of the subscription database for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-190">將 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>設為「訂閱者」的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-190">The name of the Subscriber for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-191">將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>設為步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-191">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="1c1ec-192">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得剩餘的訂閱屬性。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-192">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="1c1ec-193">如果此方法傳回 `false`，請確認該訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-193">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="1c1ec-194">以下列其中一種方式啟動「散發者」上的「散發代理程式」：</span><span class="sxs-lookup"><span data-stu-id="1c1ec-194">Start the Distribution Agent at the Distributor in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="1c1ec-195">從步驟 2 的 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> 執行個體上呼叫 <xref:Microsoft.SqlServer.Replication.TransSubscription> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-195">Call the <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.TransSubscription> from step 2.</span></span> <span data-ttu-id="1c1ec-196">此方法會以非同步方式啟動散發代理程式，並且控制項會在代理程式作業執行時立即傳回至應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-196">This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="1c1ec-197">如果訂閱是以 <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> 的 `false` 值建立的，則您將無法呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-197">You cannot call this method if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-198">從 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> 屬性取得 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> 類別的執行個體，並呼叫 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-198">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="1c1ec-199">此方法會同步啟動代理程式，而控制項仍會停留於正在執行的代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-199">This method starts the agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="1c1ec-200">在同步執行期間，您可以在代理程式執行時處理 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> 事件。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-200">During synchronous execution you can handle the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="1c1ec-201">若要同步處理合併式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="1c1ec-201">To synchronize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="1c1ec-202">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-202">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1c1ec-203">建立 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 類別的執行個體，並設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="1c1ec-203">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="1c1ec-204">將 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>設為發行集資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-204">The publication database name for <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-205">將 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>設為訂閱所屬發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-205">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-206">將 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>設為訂閱資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-206">The name of the subscription database for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-207">將 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>設為「訂閱者」的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-207">The name of the Subscriber for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-208">將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>設為步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-208">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="1c1ec-209">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得剩餘的訂閱屬性。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-209">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="1c1ec-210">如果此方法傳回 `false`，請確認該訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-210">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="1c1ec-211">以下列其中一種方式啟動「散發者」上的「合併代理程式」：</span><span class="sxs-lookup"><span data-stu-id="1c1ec-211">Start the Merge Agent at the Distributor in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="1c1ec-212">從步驟 2 的 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> 執行個體上呼叫 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-212">Call the <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.MergeSubscription> from step 2.</span></span> <span data-ttu-id="1c1ec-213">此方法會以非同步方式啟動合併代理程式，並且控制項會在代理程式作業執行時立即傳回至應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-213">This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="1c1ec-214">如果訂閱是以 <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> 的 `false` 值建立的，則您將無法呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-214">You cannot call this method if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.</span></span>  
  
    -   <span data-ttu-id="1c1ec-215">從 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> 屬性取得 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> 類別的執行個體，並呼叫 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-215">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="1c1ec-216">此方法會同步啟動「合併代理程式」，而控制項仍會停留於正在執行的代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-216">This method starts the Merge Agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="1c1ec-217">在同步執行期間，您可以在代理程式執行時處理 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> 事件。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-217">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="1c1ec-218">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="1c1ec-218">Examples (RMO)</span></span>  
 <span data-ttu-id="1c1ec-219">此範例同步處理交易式發行集的發送訂閱，其中代理程式會使用代理程式作業非同步啟動。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-219">This example synchronizes a push subscription to a transactional publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 <span data-ttu-id="1c1ec-220">此範例同步處理交易式發行集的發送訂閱，其中代理程式會同步啟動。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-220">This example synchronizes a push subscription to a transactional publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 <span data-ttu-id="1c1ec-221">此範例同步處理合併式發行集的發送訂閱，其中代理程式會使用代理程式作業非同步啟動。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-221">This example synchronizes a push subscription to a merge publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 <span data-ttu-id="1c1ec-222">此範例同步處理合併式發行集的發送訂閱，其中代理程式會同步啟動。</span><span class="sxs-lookup"><span data-stu-id="1c1ec-222">This example synchronizes a push subscription to a merge publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="1c1ec-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c1ec-223">See Also</span></span>  
 <span data-ttu-id="1c1ec-224">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="1c1ec-224">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="1c1ec-225">[同步處理資料](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="1c1ec-225">[Synchronize Data](synchronize-data.md) </span></span>  
 [<span data-ttu-id="1c1ec-226">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="1c1ec-226">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
