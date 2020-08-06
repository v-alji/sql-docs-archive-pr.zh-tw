---
title: MSSQL_ENG020554 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020554 error
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b48714f19fdec520c7bd20e4d8598d491f6e1908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702781"
---
# <a name="mssql_eng020554"></a><span data-ttu-id="1e5fa-102">MSSQL_ENG020554</span><span class="sxs-lookup"><span data-stu-id="1e5fa-102">MSSQL_ENG020554</span></span>
    
## <a name="message-details"></a><span data-ttu-id="1e5fa-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="1e5fa-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e5fa-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1e5fa-104">Product Name</span></span>|<span data-ttu-id="1e5fa-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1e5fa-105">SQL Server</span></span>|  
|<span data-ttu-id="1e5fa-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1e5fa-106">Event ID</span></span>|<span data-ttu-id="1e5fa-107">20554</span><span class="sxs-lookup"><span data-stu-id="1e5fa-107">20554</span></span>|  
|<span data-ttu-id="1e5fa-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1e5fa-108">Event Source</span></span>|<span data-ttu-id="1e5fa-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1e5fa-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1e5fa-110">元件</span><span class="sxs-lookup"><span data-stu-id="1e5fa-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="1e5fa-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1e5fa-111">Symbolic Name</span></span>||  
|<span data-ttu-id="1e5fa-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1e5fa-112">Message Text</span></span>|<span data-ttu-id="1e5fa-113">複寫代理程式已有 %ld 分鐘未記錄進度訊息。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-113">The replication agent has not logged a progress message in %ld minutes.</span></span> <span data-ttu-id="1e5fa-114">這可能表示代理程式沒有回應或系統活動量很高。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-114">This might indicate an unresponsive agent or high system activity.</span></span> <span data-ttu-id="1e5fa-115">請確認記錄正在複寫至目的地，而且到訂閱者、發行者及散發者的連接仍在使用中。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-115">Verify that records are being replicated to the destination and that connections to the Subscriber, Publisher, and Distributor are still active.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1e5fa-116">說明</span><span class="sxs-lookup"><span data-stu-id="1e5fa-116">Explanation</span></span>  
 <span data-ttu-id="1e5fa-117">**檢查複寫代理程式** 作業將在指定間隔 (依預設為10 分鐘) 執行以檢查每個複寫代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-117">The **Replication agents checkup** job runs at a specified interval (10 minutes by default) to check on the status of each replication agent.</span></span> <span data-ttu-id="1e5fa-118">如果代理程式自上次代理程式檢查作業執行以來未記錄任何進度訊息，則可能引發錯誤 MSSQL_ENG020554。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-118">If an agent has not logged any progress messages since the last time the agent checkup job ran, error MSSQL_ENG020554 can be raised.</span></span> <span data-ttu-id="1e5fa-119">如果沒有發生其他複寫活動，則該代理程式必須至少記錄記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-119">The agent is expected at least to log history messages even if no other replication activity is occurring.</span></span> <span data-ttu-id="1e5fa-120">雖然複寫代理程式未按預期回應，但這不一定代表它已停止或失敗 (如果代理程式失敗，應引發錯誤 MSSQL_ENG020536)。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-120">Although the replication agent is not responding as expected, it has not necessarily stopped or failed (if an agent has failed, error MSSQL_ENG020536 should be raised).</span></span>  
  
 <span data-ttu-id="1e5fa-121">下列問題可能導致引發錯誤 MSSQL_ENG020554：</span><span class="sxs-lookup"><span data-stu-id="1e5fa-121">The following issues can cause error MSSQL_ENG020554 to be raised:</span></span>  
  
-   <span data-ttu-id="1e5fa-122">代理程式忙碌中。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-122">The agent is busy.</span></span>  
  
     <span data-ttu-id="1e5fa-123">如果在受代理程式檢查作業輪詢期間，代理程式因太忙而無法作出回應，則代理程式檢查作業將無法報告複寫代理程式是否運作正常。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-123">If the agent is too busy to respond when polled by the agent checkup job, the agent checkup job cannot report whether the replication agent is functioning properly.</span></span> <span data-ttu-id="1e5fa-124">導致複寫代理程式忙碌的原因有很多：可能是正在複寫的資料太多，或者是應用程式設計或組態問題導致處理執行時間過長。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-124">There are a number of reasons why the replication agent could be busy: there might be a lot of data being replicated, or there might be application design or configuration issues that result in processes that run for a long time.</span></span>  
  
-   <span data-ttu-id="1e5fa-125">代理程式無法登入拓撲中的某一台電腦。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-125">The agent cannot log in to one of the computers in the topology.</span></span>  
  
     <span data-ttu-id="1e5fa-126">所有代理程式均具有參數 **-LoginTimeOut** (預設設定為 15 秒)，該參數用於控制代理程式嘗試登入複寫節點所花費的時間，例如「合併代理程式」登入「發行者」。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-126">All agents have a parameter **-LoginTimeOut** (set to 15 seconds by default), which governs how long an agent attempts to log in to a replication node, such as a Merge Agent logging in to the Publisher.</span></span> <span data-ttu-id="1e5fa-127">如果設定的 **-LoginTimeOut** 值大於複寫代理程式檢查作業執行的時間間隔，則登入問題可能是導致錯誤的根本原因：錯誤 MSSQL_ENG020554 的引發會導致代理程式引發其他特定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-127">If the **-LoginTimeOut** value is set higher than the interval at which the replication agent checkup job runs, a login problem could be the root cause of the error: error MSSQL_ENG020554 is raised before the agent is able to raise a more specific error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1e5fa-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1e5fa-128">User Action</span></span>  
 <span data-ttu-id="1e5fa-129">要求的動作視導致錯誤的原因而定：</span><span class="sxs-lookup"><span data-stu-id="1e5fa-129">The action required depends on the cause of the error:</span></span>  
  
-   <span data-ttu-id="1e5fa-130">引發此錯誤的所有情況：</span><span class="sxs-lookup"><span data-stu-id="1e5fa-130">For all cases in which this error is raised:</span></span>  
  
     <span data-ttu-id="1e5fa-131">在「複寫監視器」中檢查錯誤詳細資料，然後重新啟動代理程式 (如果它已停止)。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-131">Check the error details in Replication Monitor, and then restart the agent if it has stopped.</span></span> <span data-ttu-id="1e5fa-132">錯誤詳細資料可能會提供有關代理程式無法正確執行之原因的額外資訊。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-132">The error details might provide additional information on why the agent was not running properly.</span></span> <span data-ttu-id="1e5fa-133">如果代理程式在執行，請勿停止並重新啟動代理程式，因為這樣可能會使問題惡化。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-133">If the agent is running, do not stop and restart the agent, because that can exacerbate the problem.</span></span> <span data-ttu-id="1e5fa-134">如需有關檢視代理程式狀態以及複寫監視器中的錯誤詳細資料，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1e5fa-134">For information about viewing agent status and error details in Replication Monitor, see the following topics:</span></span>  
  
    -   <span data-ttu-id="1e5fa-135">如需快照集代理程式、記錄讀取器代理程式和佇列讀取器代理程式，請參閱[使用複寫監視器來查看資訊及執行](monitor/view-information-and-perform-tasks-replication-monitor.md)工作。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-135">For the Snapshot Agent, Log Reader Agent, and Queue Reader Agent, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
    -   <span data-ttu-id="1e5fa-136">如需散發代理程式和合併代理程式，請參閱[使用複寫監視器來查看資訊及執行](monitor/view-information-and-perform-tasks-replication-monitor.md)工作。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-136">For the Distribution Agent and Merge Agent, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="1e5fa-137">如果因代理程式正忙而頻繁出現此錯誤：</span><span class="sxs-lookup"><span data-stu-id="1e5fa-137">If this error is raised frequently because the agent is busy:</span></span>  
  
     <span data-ttu-id="1e5fa-138">您可能需要重新設計應用程式，以縮短代理程式的處理時間。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-138">You might need to redesign your application so that the agent spends less time processing.</span></span>  
  
     <span data-ttu-id="1e5fa-139">您可以使用 **[作業屬性]** 對話方塊增加檢查代理程式狀態的間隔。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-139">You can increase the interval at which agent status is checked using the **Job Properties** dialog box.</span></span> <span data-ttu-id="1e5fa-140">如需針對複寫作業存取此對話方塊的詳細資訊，請參閱[使用複寫監視器來查看資訊及執行](monitor/view-information-and-perform-tasks-replication-monitor.md)工作。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-140">For information about accessing this dialog box for replication jobs, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="1e5fa-141">如果代理程式無法登入拓撲中的某台電腦：</span><span class="sxs-lookup"><span data-stu-id="1e5fa-141">If an agent cannot log in to one of the computers in the topology:</span></span>  
  
     <span data-ttu-id="1e5fa-142">建議將 **-LoginTimeOut** 值設定為小於複寫代理程式檢查作業執行的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-142">We recommend that the **-LoginTimeOut** value be set lower than the interval at which the replication agent checkup job runs.</span></span> <span data-ttu-id="1e5fa-143">在某些情況下， **-LoginTimeOut** 的值之所以設定得高，是因為會導致登入逾時的網路問題。如果 **-LoginTimeOut** 設定得較低，則複寫會報告其他特定的問題，讓您可以對由權限、網路問題或其他問題導致的登入問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-143">In some cases, the value for **-LoginTimeOut** is set higher because of network issues that cause logins to time out. If the **-LoginTimeOut** is set lower, replication can report more specific errors, allowing you to troubleshoot login problems that could be caused by permissions, network problems, or other issues.</span></span> <span data-ttu-id="1e5fa-144">可於代理程式設定檔和命令列中指定代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-144">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="1e5fa-145">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="1e5fa-145">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="1e5fa-146">處理複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="1e5fa-146">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="1e5fa-147">檢視並修改複寫代理程式命令提示字元參數 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1e5fa-147">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="1e5fa-148">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)的最小和最大記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="1e5fa-148">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5fa-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e5fa-149">See Also</span></span>  
 <span data-ttu-id="1e5fa-150">[複寫代理程式管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="1e5fa-150">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="1e5fa-151">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="1e5fa-151">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="1e5fa-152">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1e5fa-152">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="1e5fa-153">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1e5fa-153">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="1e5fa-154">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1e5fa-154">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="1e5fa-155">[複寫佇列讀取器代理程式](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="1e5fa-155">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="1e5fa-156">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="1e5fa-156">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
