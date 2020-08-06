---
title: 在複寫監視器中設定閾值和警告 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server replication]
- Merge Agent, thresholds and warnings
- Distribution Agent, thresholds and warnings
- thresholds [SQL Server replication]
- Replication Monitor, thresholds and warnings
- monitoring performance [SQL Server replication], thresholds and warnings
ms.assetid: 3a409c2c-b77e-4001-b81a-1dcd918618ec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f34878a6398df34e55e6dd3783f2da736bee0959
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709189"
---
# <a name="set-thresholds-and-warnings-in-replication-monitor"></a><span data-ttu-id="05dfd-102">在複寫監視器中設定臨界值和警告</span><span class="sxs-lookup"><span data-stu-id="05dfd-102">Set Thresholds and Warnings in Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="05dfd-103">「複寫監視器」會顯示發行集 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 和訂閱的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="05dfd-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor displays status information for publications and subscriptions.</span></span> <span data-ttu-id="05dfd-104">依預設，複寫監視器只針對未初始化的訂閱顯示警告，但您可以啟用於其他條件下發出警告。</span><span class="sxs-lookup"><span data-stu-id="05dfd-104">By default, Replication Monitor displays warnings only for uninitialized subscriptions, but you can enable warnings for other conditions.</span></span> <span data-ttu-id="05dfd-105">建議您啟用拓撲警告，這樣您才能收到即時的狀態和效能資訊。</span><span class="sxs-lookup"><span data-stu-id="05dfd-105">It is recommended that you enable warnings for your topology, so that you are informed about status and performance in a timely manner.</span></span>  
  
 <span data-ttu-id="05dfd-106">在您啟用警告時，必須指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="05dfd-106">When you enable a warning, you specify a threshold.</span></span> <span data-ttu-id="05dfd-107">達到或超過臨界值時，會顯示警告 (除非有更高優先順序的問題需要顯示)。</span><span class="sxs-lookup"><span data-stu-id="05dfd-107">When that threshold is met or exceeded, a warning is displayed (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="05dfd-108">除了在複寫監視器顯示警告外，達到臨界值也會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="05dfd-108">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="05dfd-109">您可啟用滿足下列條件時的警告：</span><span class="sxs-lookup"><span data-stu-id="05dfd-109">You can enable warnings for the following conditions:</span></span>  
  
-   <span data-ttu-id="05dfd-110">即將發生訂閱過期</span><span class="sxs-lookup"><span data-stu-id="05dfd-110">Imminent subscription expiration</span></span>  
  
     <span data-ttu-id="05dfd-111">此條件套用於所有類型的複寫。</span><span class="sxs-lookup"><span data-stu-id="05dfd-111">This applies to all types of replication.</span></span> <span data-ttu-id="05dfd-112">如果達到或超過指定的臨界值，訂閱狀態會顯示為 **[即將過期/已過期]**。</span><span class="sxs-lookup"><span data-stu-id="05dfd-112">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired**.</span></span>  
  
-   <span data-ttu-id="05dfd-113">超過指定的延遲 (交易受發行者認可與對應交易受訂閱者認可之間所經過的時間)。</span><span class="sxs-lookup"><span data-stu-id="05dfd-113">Exceeding the specified latency (the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber).</span></span>  
  
     <span data-ttu-id="05dfd-114">這可以套用於異動複寫。</span><span class="sxs-lookup"><span data-stu-id="05dfd-114">This applies to transactional replication.</span></span> <span data-ttu-id="05dfd-115">如果達到或超過指定臨界值，訂閱狀態將顯示為 **[效能嚴重不足]**。</span><span class="sxs-lookup"><span data-stu-id="05dfd-115">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical**.</span></span>  
  
-   <span data-ttu-id="05dfd-116">超過指定的同步處理時間。</span><span class="sxs-lookup"><span data-stu-id="05dfd-116">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="05dfd-117">這可以套用於合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="05dfd-117">This applies to merge replication.</span></span> <span data-ttu-id="05dfd-118">若已達到或超過指定臨界值，狀態顯示為 **[長期執行合併]**。</span><span class="sxs-lookup"><span data-stu-id="05dfd-118">If the specified threshold is met or exceeded, the status is displayed as **Long-running merge**.</span></span> <span data-ttu-id="05dfd-119">您可以為撥號連接和區域網路 (LAN) 連接，指定不同的臨界值。</span><span class="sxs-lookup"><span data-stu-id="05dfd-119">You can specify different thresholds for dialup and Local Area Network (LAN) connections.</span></span>  
  
-   <span data-ttu-id="05dfd-120">在給定時間內處理的資料列數達不到指定數目。</span><span class="sxs-lookup"><span data-stu-id="05dfd-120">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="05dfd-121">這可以套用於合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="05dfd-121">This applies to merge replication.</span></span> <span data-ttu-id="05dfd-122">若已達到或超過指定臨界值，狀態顯示為 **[效能嚴重不足]**。</span><span class="sxs-lookup"><span data-stu-id="05dfd-122">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span> <span data-ttu-id="05dfd-123">您可以為撥號連接和 LAN 連接，指定不同的臨界值。</span><span class="sxs-lookup"><span data-stu-id="05dfd-123">You can specify different thresholds for dialup and LAN connections.</span></span>  
  
 <span data-ttu-id="05dfd-124">如需 [效能嚴重不足]\*\*\*\* 和 [長期執行合併]\*\*\*\* 警告的詳細資訊，請參閱[使用複寫監視器監視效能](monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="05dfd-124">For more information on the warnings **Performance critical** and **Long-running merge**, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="05dfd-125">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="05dfd-125">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="05dfd-126">設定交易式發行集的臨界值與警告</span><span class="sxs-lookup"><span data-stu-id="05dfd-126">Set thresholds and warnings for a transactional publication</span></span>](#Transactional)  
  
-   [<span data-ttu-id="05dfd-127">設定合併式發行集的臨界值和警告</span><span class="sxs-lookup"><span data-stu-id="05dfd-127">Set thresholds and warnings for a merge publication</span></span>](#Merge)  
  
-   [<span data-ttu-id="05dfd-128">設定快照式發行集的臨界值和警告</span><span class="sxs-lookup"><span data-stu-id="05dfd-128">Set thresholds and warnings for a snapshot publication</span></span>](#Snapshot)  
  
##  <a name="to-set-thresholds-and-warnings-for-a-transactional-publication"></a><a name="Transactional"></a> <span data-ttu-id="05dfd-129">若要設定交易式發行集的臨界值與警告</span><span class="sxs-lookup"><span data-stu-id="05dfd-129">To set thresholds and warnings for a transactional publication</span></span>  
  
1.  <span data-ttu-id="05dfd-130">在左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="05dfd-130">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="05dfd-131">按一下 [**警告**] 索引標籤。若要查看此索引標籤上選項的詳細資訊 **，請按一下功能表列上的**[說明]。</span><span class="sxs-lookup"><span data-stu-id="05dfd-131">Click the **Warnings** tab. To view more information about the options on this tab click **Help** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="05dfd-132">透過選取適當的核取方塊啟用警告： **[若訂閱將在臨界值內過期，就發出警告]** 或 **[若延遲超過臨界值，就發出警告]**。</span><span class="sxs-lookup"><span data-stu-id="05dfd-132">Enable a warning by selecting the appropriate check box: **Warn if a subscription will expire within the threshold** or **Warn if latency exceeds the threshold**.</span></span>  
  
4.  <span data-ttu-id="05dfd-133">在 **[臨界值]** 資料行中設定警告的臨界值。</span><span class="sxs-lookup"><span data-stu-id="05dfd-133">Set a threshold for the warnings in the **Threshold** column.</span></span> <span data-ttu-id="05dfd-134">例如，如果您在步驟 3 選取 **[若延遲超過臨界值，就發出警告]** ，便可以在 **[臨界值]** 資料行中選取 **[60 秒]** 的延遲。</span><span class="sxs-lookup"><span data-stu-id="05dfd-134">For example, if you selected **Warn if latency exceeds the threshold** in step 3, you could select a latency of **60 seconds** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="05dfd-135">按一下 **[儲存變更]** 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-135">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="05dfd-136">若要設定臨界值的警示</span><span class="sxs-lookup"><span data-stu-id="05dfd-136">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="05dfd-137">按一下 **[設定警示]**。</span><span class="sxs-lookup"><span data-stu-id="05dfd-137">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="05dfd-138">在 **[設定複寫警示]** 對話方塊中選取一個警示，然後按一下 **[設定]** 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-138">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="05dfd-139">這個對話方塊會顯示所有發行集類型的警示，包括與監視臨界值無關的警示。</span><span class="sxs-lookup"><span data-stu-id="05dfd-139">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span> <span data-ttu-id="05dfd-140">如需詳細資訊，請參閱[使用複寫代理程式事件的警示](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="05dfd-140">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
3.  <span data-ttu-id="05dfd-141">在 [\<AlertName> 警示屬性] 對話方塊中設定選項：</span><span class="sxs-lookup"><span data-stu-id="05dfd-141">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="05dfd-142">在 **[一般]** 頁面上，按一下 **[啟用]** ；指定警示應套用至哪個資料庫。</span><span class="sxs-lookup"><span data-stu-id="05dfd-142">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="05dfd-143">在 **[回應]** 頁面上，指定是否應傳送電子郵件及 (或) 是否應執行作業。</span><span class="sxs-lookup"><span data-stu-id="05dfd-143">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="05dfd-144">在 **[選項]** 頁面上，自訂回應的文字。</span><span class="sxs-lookup"><span data-stu-id="05dfd-144">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="05dfd-145">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-145">Click **Close**.</span></span>  
  
##  <a name="set-thresholds-and-warnings-for-a-merge-publication"></a><a name="Merge"></a><span data-ttu-id="05dfd-146">設定合併式發行集的臨界值和警告</span><span class="sxs-lookup"><span data-stu-id="05dfd-146">Set thresholds and warnings for a merge publication</span></span>  
  
1.  <span data-ttu-id="05dfd-147">在左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="05dfd-147">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="05dfd-148">按一下 [**警告**] 索引標籤。若要查看此索引標籤上選項的詳細資訊，**請按一下功能表**欄上的 [說明]。</span><span class="sxs-lookup"><span data-stu-id="05dfd-148">Click the **Warnings** tab. To view more information about the options on this tab, click **Help** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="05dfd-149">透過選取適當的核取方塊啟用警告：</span><span class="sxs-lookup"><span data-stu-id="05dfd-149">Enable a warning by selecting the appropriate check box:</span></span>  
  
    -   <span data-ttu-id="05dfd-150">**[若訂閱將在臨界值內過期，就發出警告]**</span><span class="sxs-lookup"><span data-stu-id="05dfd-150">**Warn if a subscription will expire within the threshold**</span></span>  
  
    -   <span data-ttu-id="05dfd-151">**如果撥號連接的合併長度超過臨界值，則發出警告**</span><span class="sxs-lookup"><span data-stu-id="05dfd-151">**Warn if a merge length for dialup connections exceeds the threshold**</span></span>  
  
    -   <span data-ttu-id="05dfd-152">**如果 LAN 連接的合併長度超過臨界值，則發出警告**</span><span class="sxs-lookup"><span data-stu-id="05dfd-152">**Warn if a merge length for LAN connections exceeds the threshold**</span></span>  
  
    -   <span data-ttu-id="05dfd-153">**如果 LAN 連接的每秒合併資料列少於臨界值，則發出警告**</span><span class="sxs-lookup"><span data-stu-id="05dfd-153">**Warn if rows merged per second for LAN connections is less than the threshold**</span></span>  
  
    -   <span data-ttu-id="05dfd-154">**如果撥號連接之每秒的合併資料列少於臨界值，則發出警告**</span><span class="sxs-lookup"><span data-stu-id="05dfd-154">**Warn if rows merged per second for dialup connections is less than the threshold**</span></span>  
  
4.  <span data-ttu-id="05dfd-155">在 **[臨界值]** 資料行中設定警告的臨界值。</span><span class="sxs-lookup"><span data-stu-id="05dfd-155">Set thresholds for the warnings in the **Threshold** column.</span></span> <span data-ttu-id="05dfd-156">例如，如果您在步驟 3 選取 **[若撥號連接的合併長度超過臨界值，就發出警告]** ，便可以在 **[臨界值]** 資料行中選取 **[10 分鐘]** 的時間。</span><span class="sxs-lookup"><span data-stu-id="05dfd-156">For example, if you selected **Warn if a merge length for dialup connections exceeds the threshold** in step 3, you could select a time of **10 minutes** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="05dfd-157">按一下 **[儲存變更]** 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-157">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="05dfd-158">若要設定臨界值的警示</span><span class="sxs-lookup"><span data-stu-id="05dfd-158">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="05dfd-159">按一下 **[設定警示]**。</span><span class="sxs-lookup"><span data-stu-id="05dfd-159">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="05dfd-160">在 **[設定複寫警示]** 對話方塊中選取一個警示，然後按一下 **[設定]** 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-160">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="05dfd-161">這個對話方塊會顯示所有發行集類型的警示，包括與監視臨界值無關的警示。</span><span class="sxs-lookup"><span data-stu-id="05dfd-161">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span>  
  
3.  <span data-ttu-id="05dfd-162">在 [\<AlertName> 警示屬性] 對話方塊中設定選項：</span><span class="sxs-lookup"><span data-stu-id="05dfd-162">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="05dfd-163">在 **[一般]** 頁面上，按一下 **[啟用]** ；指定警示應套用至哪個資料庫。</span><span class="sxs-lookup"><span data-stu-id="05dfd-163">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="05dfd-164">在 **[回應]** 頁面上，指定是否應傳送電子郵件及 (或) 是否應執行作業。</span><span class="sxs-lookup"><span data-stu-id="05dfd-164">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="05dfd-165">在 **[選項]** 頁面上，自訂回應的文字。</span><span class="sxs-lookup"><span data-stu-id="05dfd-165">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="05dfd-166">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-166">Click **Close**.</span></span>  
  
##  <a name="set-thresholds-and-warnings-for-a-snapshot-publication"></a><a name="Snapshot"></a><span data-ttu-id="05dfd-167">設定快照式發行集的臨界值和警告</span><span class="sxs-lookup"><span data-stu-id="05dfd-167">Set thresholds and warnings for a snapshot publication</span></span>  
  
1.  <span data-ttu-id="05dfd-168">在左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="05dfd-168">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="05dfd-169">按一下 [**警告**] 索引標籤。若要查看此索引標籤上選項的詳細資訊 **，請按一下上方功能表上的**[說明]。</span><span class="sxs-lookup"><span data-stu-id="05dfd-169">Click the **Warnings** tab. To view more information about the options on this tab click **Help** on the top menu.</span></span>  
  
3.  <span data-ttu-id="05dfd-170">透過選取 **[若訂閱將在臨界值內過期，就發出警告]** 核取方塊啟用警告。</span><span class="sxs-lookup"><span data-stu-id="05dfd-170">Enable a warning by selecting the check box **Warn if a subscription will expire within the threshold**.</span></span>  
  
4.  <span data-ttu-id="05dfd-171">在 **[臨界值]** 資料行中設定警告的臨界值。</span><span class="sxs-lookup"><span data-stu-id="05dfd-171">Set a threshold for the warning in the **Threshold** column.</span></span> <span data-ttu-id="05dfd-172">例如，可在 **[臨界值]** 資料行中選取值 **[70%]** 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-172">For example, you could select a value of **70%** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="05dfd-173">按一下 **[儲存變更]** 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-173">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="05dfd-174">若要設定臨界值的警示</span><span class="sxs-lookup"><span data-stu-id="05dfd-174">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="05dfd-175">按一下 **[設定警示]**。</span><span class="sxs-lookup"><span data-stu-id="05dfd-175">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="05dfd-176">在 **[設定複寫警示]** 對話方塊中選取一個警示，然後按一下 **[設定]** 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-176">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="05dfd-177">這個對話方塊會顯示所有發行集類型的警示，包括與監視臨界值無關的警示。</span><span class="sxs-lookup"><span data-stu-id="05dfd-177">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span> <span data-ttu-id="05dfd-178">如需詳細資訊，請參閱[使用複寫代理程式事件的警示](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="05dfd-178">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
3.  <span data-ttu-id="05dfd-179">在 [\<AlertName> 警示屬性] 對話方塊中設定選項：</span><span class="sxs-lookup"><span data-stu-id="05dfd-179">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="05dfd-180">在 **[一般]** 頁面上，按一下 **[啟用]** ；指定警示應套用至哪個資料庫。</span><span class="sxs-lookup"><span data-stu-id="05dfd-180">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="05dfd-181">在 **[回應]** 頁面上，指定是否應傳送電子郵件及 (或) 是否應執行作業。</span><span class="sxs-lookup"><span data-stu-id="05dfd-181">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="05dfd-182">在 **[選項]** 頁面上，自訂回應的文字。</span><span class="sxs-lookup"><span data-stu-id="05dfd-182">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="05dfd-183">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="05dfd-183">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05dfd-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05dfd-184">See Also</span></span>  
 [<span data-ttu-id="05dfd-185">監視複寫</span><span class="sxs-lookup"><span data-stu-id="05dfd-185">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
