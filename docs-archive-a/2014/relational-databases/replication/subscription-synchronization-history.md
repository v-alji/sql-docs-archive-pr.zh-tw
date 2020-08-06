---
title: 訂閱、同步處理歷程記錄 (合併訂閱、SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.synchhistory.f1
- sql12.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 85f666f6-14ee-4f19-b385-e5cc508aabe4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49fe19f22976116813ac2454b2d08fc1fe47d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598815"
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2005-and-later"></a><span data-ttu-id="3ccb2-102">訂閱，同步處理記錄 (合併訂閱，SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="3ccb2-102">Subscription, Synchronization History (Merge Subscription, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="3ccb2-103">**[同步處理記錄]** 索引標籤會顯示有關合併代理程式的詳細資訊，包括狀態、發行項統計資料、記錄、參考訊息和錯誤訊息等等。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-103">The **Synchronization History** tab displays detailed information on the Merge Agent, including status, article statistics, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ccb2-104">選項。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-104">Options</span></span>  
 <span data-ttu-id="3ccb2-105">從 **[檢視]** 功能表中選取要檢視的合併代理程式工作階段，再於 **[合併代理程式工作階段]** 方格中選取特定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-105">Select which Merge Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Merge Agent**.</span></span> <span data-ttu-id="3ccb2-106">有關這個工作階段的詳細資訊，會顯示在標示為 **[在選取的工作階段中處理的發行項]** 的方格中。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-106">Detailed information on this session is displayed in the grid labeled **Articles processed in the selected session**.</span></span>  
  
 <span data-ttu-id="3ccb2-107">**檢視**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-107">**View**</span></span>  
 <span data-ttu-id="3ccb2-108">選取要檢視的合併代理程式工作階段。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-108">Select which Merge Agent sessions to view.</span></span>  
  
 <span data-ttu-id="3ccb2-109">**狀態**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-109">**Status**</span></span>  
 <span data-ttu-id="3ccb2-110">工作階段結束時的合併代理程式狀態。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-110">The status of the Merge Agent at the end of the session.</span></span> <span data-ttu-id="3ccb2-111">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="3ccb2-111">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="3ccb2-112">錯誤</span><span class="sxs-lookup"><span data-stu-id="3ccb2-112">Error</span></span>  
  
-   <span data-ttu-id="3ccb2-113">Completed</span><span class="sxs-lookup"><span data-stu-id="3ccb2-113">Completed</span></span>  
  
-   <span data-ttu-id="3ccb2-114">正在重試</span><span class="sxs-lookup"><span data-stu-id="3ccb2-114">Retrying</span></span>  
  
-   <span data-ttu-id="3ccb2-115">執行中</span><span class="sxs-lookup"><span data-stu-id="3ccb2-115">Running</span></span>  
  
 <span data-ttu-id="3ccb2-116">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-116">**Start Time**</span></span>  
 <span data-ttu-id="3ccb2-117">工作階段的開始時間。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-117">The start time of the session.</span></span>  
  
 <span data-ttu-id="3ccb2-118">**結束時間**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-118">**End Time**</span></span>  
 <span data-ttu-id="3ccb2-119">工作階段的結束時間。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-119">The end time of the session.</span></span> <span data-ttu-id="3ccb2-120">如果代理程式未停止，則這個欄位是空的。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-120">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="3ccb2-121">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-121">**Duration**</span></span>  
 <span data-ttu-id="3ccb2-122">合併代理程式在工作階段中執行的時間量。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-122">The amount of time the Merge Agent has run in a session.</span></span> <span data-ttu-id="3ccb2-123">如果代理程式目前正在執行，此時間代表經過時間；如果代理程式是先前有執行過，則此時間代表總共時間。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-123">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="3ccb2-124">**已上傳的命令**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-124">**Uploaded Commands**</span></span>  
 <span data-ttu-id="3ccb2-125">在合併代理程式工作階段期間，已上傳的資料列數。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-125">The number of rows uploaded during the Merge Agent session.</span></span>  
  
 <span data-ttu-id="3ccb2-126">**已下載命令**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-126">**Downloaded Commands**</span></span>  
 <span data-ttu-id="3ccb2-127">在合併代理程式工作階段期間，已下載的資料列數。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-127">The number of rows downloaded during the Merge Agent session.</span></span>  
  
 <span data-ttu-id="3ccb2-128">**錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-128">**Error Message**</span></span>  
 <span data-ttu-id="3ccb2-129">如果工作階段結束時發生錯誤，這個欄位會顯示合併代理程式記錄的最後一個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-129">If a session ended in an error, this field displays the last error message logged by the Merge Agent.</span></span> <span data-ttu-id="3ccb2-130">如果工作階段結束時沒有錯誤，這個欄位會是空白。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-130">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="3ccb2-131">**文章**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-131">**Article**</span></span>  
 <span data-ttu-id="3ccb2-132">發行集內每個發行項的名稱，以及整個發行集的下列處理階段：</span><span class="sxs-lookup"><span data-stu-id="3ccb2-132">The name of each article in the publication, and the following processing phases for the entire publication:</span></span>  
  
-   <span data-ttu-id="3ccb2-133">**初始化**。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-133">**Initialization**.</span></span> <span data-ttu-id="3ccb2-134">這是指合併代理程式的啟動；而不是涉及套用快照集的訂閱之初始化。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-134">This refers to starting the Merge Agent; this is not synonymous with initializing a subscription, which involves applying a snapshot.</span></span>  
  
-   <span data-ttu-id="3ccb2-135">**結構描述變更及大量插入**。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-135">**Schema changes and bulk inserts**.</span></span>  
  
-   <span data-ttu-id="3ccb2-136">**將變更上傳至發行者**。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-136">**Upload changes to Publisher**.</span></span>  
  
-   <span data-ttu-id="3ccb2-137">**下載變更到訂閱者**。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-137">**Download changes to Subscriber**.</span></span>  
  
 <span data-ttu-id="3ccb2-138">方格中會包含這些階段，方格才能顯示所選取工作階段內、每個階段所花費時間量以及其時間量佔總時間量的百分比。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-138">The phases are included so that the grid can display the amount of time and percentage of total time that each phase accounts for in the selected session.</span></span>  
  
 <span data-ttu-id="3ccb2-139">**總計的 %**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-139">**% of total**</span></span>  
 <span data-ttu-id="3ccb2-140">所選取工作階段內、每個階段所花費時間量佔總處理時間的百分比。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-140">The percentage of total processing time that each phase accounts for in the selected session.</span></span>  
  
 <span data-ttu-id="3ccb2-141">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-141">**Duration**</span></span>  
 <span data-ttu-id="3ccb2-142">每個處理階段所花費的時間量。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-142">The amount of time spent in each processing phase.</span></span> <span data-ttu-id="3ccb2-143">如果合併代理程式目前正在工作階段中執行，則時間代表經過時間，如果合併代理程式先前已執行過，則時間代表總共花費的時間。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-143">The time represents elapsed time if the Merge Agent is currently running for the session and total time if the Merge Agent has run previously.</span></span>  
  
 <span data-ttu-id="3ccb2-144">**Inserts**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-144">**Inserts**</span></span>  
 <span data-ttu-id="3ccb2-145">在所選取工作階段的此階段中插入之資料列數。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-145">The number of rows inserted in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="3ccb2-146">**更新**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-146">**Updates**</span></span>  
 <span data-ttu-id="3ccb2-147">在所選取工作階段的此階段中更新之資料列數。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-147">The number of rows updated in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="3ccb2-148">**Deletes**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-148">**Deletes**</span></span>  
 <span data-ttu-id="3ccb2-149">在所選取工作階段的此階段中刪除之資料列數。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-149">The number of rows deleted in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="3ccb2-150">**衝突**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-150">**Conflicts**</span></span>  
 <span data-ttu-id="3ccb2-151">在所選取工作階段中的衝突數目。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-151">The number of conflicts in the selected session.</span></span>  
  
 <span data-ttu-id="3ccb2-152">**結構描述變更**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-152">**Schema Changes**</span></span>  
 <span data-ttu-id="3ccb2-153">在所選取工作階段中的結構描述變更數目。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-153">The number of schema changes in the selected session.</span></span> <span data-ttu-id="3ccb2-154">結構描述變更可能是因為：發行集資料庫複寫了結構描述變更；發行項的加入或卸除；以及發行項或發行集屬性的變更。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-154">Schema changes can result from: schema changes being replicated from the publication database; adding or dropping articles; and changes to article or publication properties.</span></span>  
  
 <span data-ttu-id="3ccb2-155">**所選取工作階段的最後訊息**</span><span class="sxs-lookup"><span data-stu-id="3ccb2-155">**Last message of the selected session**</span></span>  
 <span data-ttu-id="3ccb2-156">這個文字區域會顯示所選取工作階段的最後訊息。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-156">This text area displays the last message in the selected session.</span></span> <span data-ttu-id="3ccb2-157">如果發生錯誤，它會顯示錯誤的詳細資訊和發生錯誤時所嘗試的命令。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-157">If an error has occurred, it displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="3ccb2-158">它也會包括與錯誤相關之其他內容的連結。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-158">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ccb2-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ccb2-159">See Also</span></span>  
 <span data-ttu-id="3ccb2-160">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3ccb2-160">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="3ccb2-161">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3ccb2-161">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="3ccb2-162">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="3ccb2-162">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="3ccb2-163">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="3ccb2-163">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
