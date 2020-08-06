---
title: 管理 CDC 執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- manIns
ms.assetid: cfed22c8-c666-40ca-9e73-24d93e85ba92
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9b8d750c417cf5efda3f0d376151c30b6da1eb3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593512"
---
# <a name="manage-a-cdc-instance"></a><span data-ttu-id="90c84-102">管理 CDC 執行個體</span><span class="sxs-lookup"><span data-stu-id="90c84-102">Manage a CDC Instance</span></span>
  <span data-ttu-id="90c84-103">您可以使用 CDC 設計工具主控台來檢視有關您所建立之執行個體的資訊，並管理執行個體的操作。</span><span class="sxs-lookup"><span data-stu-id="90c84-103">You can use the CDC Designer Console to view information about the instances that you create and to manage the operation of the instances.</span></span>  
  
 <span data-ttu-id="90c84-104">在左窗格中按一下執行個體的名稱，以檢視有關此執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-104">Click on the name of an instance in the left pane to view the information about the instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90c84-105">如果您在左窗格中選取服務，可用執行個體的清單也會顯示在 CDC 設計工具主控台的中央。</span><span class="sxs-lookup"><span data-stu-id="90c84-105">If you select a service in the left pane, the list of available instances is also displayed in the center of the CDC Designer Console.</span></span> <span data-ttu-id="90c84-106">如果您在此區段中選取其中一個執行個體，您可以在右窗格執行工作；但是，您將無法檢視屬性索引標籤中的資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-106">If you select one of the instances in this section, you can carry out the tasks in the right pane; however, you will not be able to view the information in the property tabs.</span></span>  
  
## <a name="what-you-can-do-when-you-display-the-cdc-instance-information"></a><span data-ttu-id="90c84-107">您在顯示 CDC 執行個體資訊時可以做什麼事</span><span class="sxs-lookup"><span data-stu-id="90c84-107">What you can do when you display the CDC Instance information</span></span>  
 <span data-ttu-id="90c84-108">從右窗格執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="90c84-108">The following actions are carried out from the right pane:</span></span>  
  
 <span data-ttu-id="90c84-109">**啟動**</span><span class="sxs-lookup"><span data-stu-id="90c84-109">**Start**</span></span>  
 <span data-ttu-id="90c84-110">按一下 [啟動]  ，開始擷取選定 CDC 執行個體的變更。</span><span class="sxs-lookup"><span data-stu-id="90c84-110">Click **Start** to start the capturing changes for the selected CDC instance.</span></span>  
  
 <span data-ttu-id="90c84-111">**停止**</span><span class="sxs-lookup"><span data-stu-id="90c84-111">**Stop**</span></span>  
 <span data-ttu-id="90c84-112">按一下 [停止]  ，停止擷取選定 CDC 執行個體的變更。</span><span class="sxs-lookup"><span data-stu-id="90c84-112">Click **Stop** to stop capturing changes for the selected CDC instance.</span></span> <span data-ttu-id="90c84-113">當您停止 CDC 執行個體時，擷取至該點的變更不會遺失，而且在 CDC 執行個體恢復時會傳遞這些變更。</span><span class="sxs-lookup"><span data-stu-id="90c84-113">When you stop the CDC instance, the changes that were captured to that point are not lost and are delivered when the CDC instance is resumed.</span></span>  
  
 <span data-ttu-id="90c84-114">**重設**</span><span class="sxs-lookup"><span data-stu-id="90c84-114">**Reset**</span></span>  
 <span data-ttu-id="90c84-115">按一下 [重設]  ，將 CDC 執行個體重設為初始 (空白) 狀態。</span><span class="sxs-lookup"><span data-stu-id="90c84-115">Click **Reset** to reset the CDC instance to its initial (empty) state.</span></span> <span data-ttu-id="90c84-116">當 CDC 執行個體停止時可以使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="90c84-116">This option is available when the CDC instance is stopped.</span></span> <span data-ttu-id="90c84-117">變更資料表及 CDC 執行個體內部狀態的所有變更都會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="90c84-117">All changes in the change tables and the CDC instance internal state are deleted.</span></span> <span data-ttu-id="90c84-118">之後啟動 CDC 執行個體時，異動擷取將會從該時間點開始，而且只包含 CDC 執行個體啟動之後所開始的交易。</span><span class="sxs-lookup"><span data-stu-id="90c84-118">When the CDC instance is started later, the change capture starts from that point in time and only includes transactions that started after the CDC instance started.</span></span>  
  
 <span data-ttu-id="90c84-119">在確認對話方塊中按一下 **[確定]** ，確認您想要重設 CDC 執行個體，並刪除寫入變更資料表的變更。</span><span class="sxs-lookup"><span data-stu-id="90c84-119">Click **OK** in the confirmation dialog box to confirm that you want to reset the CDC instance and delete the changes written to the change tables.</span></span>  
  
 <span data-ttu-id="90c84-120">**刪除**</span><span class="sxs-lookup"><span data-stu-id="90c84-120">**Delete**</span></span>  
 <span data-ttu-id="90c84-121">按一下 [刪除]  ，永久刪除 CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="90c84-121">Click **Delete** to delete the CDC instance permanently.</span></span> <span data-ttu-id="90c84-122">只有當 CDC 執行個體停止時才可以使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="90c84-122">This option is available only when the CDC instance is stopped.</span></span>  
  
 <span data-ttu-id="90c84-123">在確認對話方塊中按一下 **[確定]** ，確認您想要刪除 CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="90c84-123">Click **OK** in the confirmation dialog box to confirm that you want to delete the CDC instance.</span></span>  
  
 <span data-ttu-id="90c84-124">**Oracle 記錄指令碼**</span><span class="sxs-lookup"><span data-stu-id="90c84-124">**Oracle Logging Script**</span></span>  
 <span data-ttu-id="90c84-125">按一下這個連結可顯示 [Oracle 記錄指令碼] 對話方塊，其中包含 Oracle 補充記錄指令碼。</span><span class="sxs-lookup"><span data-stu-id="90c84-125">Click this link to display the Oracle Logging script dialog box with the Oracle supplemental-logging script.</span></span> <span data-ttu-id="90c84-126">如需有關您可以在此對話方塊中執行之操作的詳細資訊，請參閱＜ [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md)＞。</span><span class="sxs-lookup"><span data-stu-id="90c84-126">For information on what you can do in this dialog box, see [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90c84-127">當您執行補充記錄指令碼時，將會開啟 [執行指令碼的 Oracle 認證] 對話方塊，您可以在此提供有效的 Oracle 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="90c84-127">When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="90c84-128">如需有關如何提供適當之 Oracle 認證的詳細資訊，請參閱＜ [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)＞。</span><span class="sxs-lookup"><span data-stu-id="90c84-128">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
 <span data-ttu-id="90c84-129">**CDC 執行個體部署指令碼**</span><span class="sxs-lookup"><span data-stu-id="90c84-129">**CDC Instance Deployment Script**</span></span>  
 <span data-ttu-id="90c84-130">按一下這個連結可顯示 [CDC 執行個體部署指令碼] 對話方塊，此對話方塊會顯示 CDC 執行個體部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="90c84-130">Click this link to display the CDC Instance Deployment Script dialog box that displays the CDC instance deployment script.</span></span> <span data-ttu-id="90c84-131">如需有關此對話方塊的詳細資訊，請參閱＜ [CDC Instance Deployment Script](cdc-instance-deployment-script.md)＞。</span><span class="sxs-lookup"><span data-stu-id="90c84-131">For information about this dialog box, see [CDC Instance Deployment Script](cdc-instance-deployment-script.md).</span></span>  
  
 <span data-ttu-id="90c84-132">**屬性**</span><span class="sxs-lookup"><span data-stu-id="90c84-132">**Properties**</span></span>  
 <span data-ttu-id="90c84-133">按一下此連結即可開啟屬性編輯器。</span><span class="sxs-lookup"><span data-stu-id="90c84-133">Click this link to open the property editor.</span></span> <span data-ttu-id="90c84-134">您可使用屬性編輯器來編輯 CDC 執行個體組態。</span><span class="sxs-lookup"><span data-stu-id="90c84-134">You edit the CDC instance configuration using the property editor.</span></span> <span data-ttu-id="90c84-135">如需有關編輯 CDC 執行個體之屬性的詳細資訊，請參閱＜ [Edit Instance Properties](edit-instance-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="90c84-135">For more information about editing the properties for a CDC instance, see [Edit Instance Properties](edit-instance-properties.md).</span></span>  
  
 <span data-ttu-id="90c84-136">**檢視器索引標籤**</span><span class="sxs-lookup"><span data-stu-id="90c84-136">**Viewer Tabs**</span></span>  
  
 <span data-ttu-id="90c84-137">當您檢視 CDC 執行個體的資訊時，可使用以下的檢視器索引標籤。</span><span class="sxs-lookup"><span data-stu-id="90c84-137">The following Viewer tabs are available when you view information for the CDC instance.</span></span> <span data-ttu-id="90c84-138">這些索引標籤中的資訊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="90c84-138">The information in these tabs is read only.</span></span>  
  
 <span data-ttu-id="90c84-139">**狀態**</span><span class="sxs-lookup"><span data-stu-id="90c84-139">**Status**</span></span>  
 <span data-ttu-id="90c84-140">此索引標籤會提供有關 CDC 執行個體目前狀態的資訊和統計資料。</span><span class="sxs-lookup"><span data-stu-id="90c84-140">This tab provides information and statistics about the CDC instance current status.</span></span> <span data-ttu-id="90c84-141">其中包含以下資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-141">It contains the following information.</span></span>  
  
-   <span data-ttu-id="90c84-142">**狀態**：指示 CDC 執行個體之目前狀態的圖示。</span><span class="sxs-lookup"><span data-stu-id="90c84-142">**Status**: An icon that indicates the current status for the CDC instance.</span></span> <span data-ttu-id="90c84-143">下面會描述這些狀態。</span><span class="sxs-lookup"><span data-stu-id="90c84-143">The following describes the statuses.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="90c84-144">![錯誤](../media/error.gif "錯誤")</span><span class="sxs-lookup"><span data-stu-id="90c84-144">![Error](../media/error.gif "Error")</span></span>|<span data-ttu-id="90c84-145">**Error**。</span><span class="sxs-lookup"><span data-stu-id="90c84-145">**Error**.</span></span> <span data-ttu-id="90c84-146">Oracle CDC 執行個體未在執行中，因為發生無法重試的錯誤。</span><span class="sxs-lookup"><span data-stu-id="90c84-146">The Oracle CDC Instance is not running because a non-retryable error occurred.</span></span> <span data-ttu-id="90c84-147">以下是可用的子狀態：</span><span class="sxs-lookup"><span data-stu-id="90c84-147">The following sub-statuses are available:</span></span><br /><br /> <span data-ttu-id="90c84-148">**設定錯誤**：發生了需要手動介入的設定錯誤。</span><span class="sxs-lookup"><span data-stu-id="90c84-148">**Misconfigured**: A configuration error occurred that requires manual intervention.</span></span><br /><br /> <span data-ttu-id="90c84-149">**需要密碼**：未針對 Oracle CDC 執行個體設定任何密碼，或是密碼無效。</span><span class="sxs-lookup"><span data-stu-id="90c84-149">**Password Required**: No password was set for the Oracle CDC Instance or the password is not valid.</span></span><br /><br /> <span data-ttu-id="90c84-150">**非預期**：</span><span class="sxs-lookup"><span data-stu-id="90c84-150">**Unexpected**.</span></span> <span data-ttu-id="90c84-151">所有其他無法復原的錯誤。</span><span class="sxs-lookup"><span data-stu-id="90c84-151">All other non-recoverable errors.</span></span>|  
    |<span data-ttu-id="90c84-152">![確定](../media/okay.gif "確定")</span><span class="sxs-lookup"><span data-stu-id="90c84-152">![Okay](../media/okay.gif "Okay")</span></span>|<span data-ttu-id="90c84-153">**執行中**：CDC 執行個體正在執行及處理變更記錄。</span><span class="sxs-lookup"><span data-stu-id="90c84-153">**Running**: The CDC Instance is running and is processing change records.</span></span> <span data-ttu-id="90c84-154">以下是可用的子狀態。</span><span class="sxs-lookup"><span data-stu-id="90c84-154">The following sub-statuses are available.</span></span><br /><br /> <span data-ttu-id="90c84-155">**閒置**：所有變更記錄都已經處理並儲存在目標變更資料表中。</span><span class="sxs-lookup"><span data-stu-id="90c84-155">**Idle**: All change records have been processed and stored in the target change tables.</span></span> <span data-ttu-id="90c84-156">沒有其他使用中交易。</span><span class="sxs-lookup"><span data-stu-id="90c84-156">There are no more active transactions.</span></span><br /><br /> <span data-ttu-id="90c84-157">**正在處理**：有正在處理但是尚未寫入變更資料表的變更記錄。</span><span class="sxs-lookup"><span data-stu-id="90c84-157">**Processing**: There are change records being process that are not yet written to the change tables.</span></span>|  
    |<span data-ttu-id="90c84-158">![停止](../media/stop.gif "Stop")</span><span class="sxs-lookup"><span data-stu-id="90c84-158">![Stop](../media/stop.gif "Stop")</span></span>|<span data-ttu-id="90c84-159">**已停止**：CDC 執行個體未在執行中。</span><span class="sxs-lookup"><span data-stu-id="90c84-159">**Stopped**: The CDC instance is not running.</span></span> <span data-ttu-id="90c84-160">已停止的狀態表示 CDC 執行個體以正常方式停止。</span><span class="sxs-lookup"><span data-stu-id="90c84-160">The stopped status indicates that the CDC instance was stopped in a normal manner.</span></span>|  
    |<span data-ttu-id="90c84-161">![已暫停](../media/paused.gif "已暫停")</span><span class="sxs-lookup"><span data-stu-id="90c84-161">![Paused](../media/paused.gif "Paused")</span></span>|<span data-ttu-id="90c84-162">**已暫停**：CDC 執行個體正在執行中，但是因為發生可重試的錯誤所以暫停處理。</span><span class="sxs-lookup"><span data-stu-id="90c84-162">**Paused**: The CDC instance is running but processing is suspended because of a retryable error.</span></span> <span data-ttu-id="90c84-163">以下是可用的子狀態：</span><span class="sxs-lookup"><span data-stu-id="90c84-163">The following sub-statuses are available:</span></span><br /><br /> <span data-ttu-id="90c84-164">**已中斷連線**：無法建立與來源 Oracle 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="90c84-164">**Disconnected**: The connection to the source Oracle database cannot be established.</span></span> <span data-ttu-id="90c84-165">還原連接時，處理作業便會繼續。</span><span class="sxs-lookup"><span data-stu-id="90c84-165">Processing resumes when the connection is restored.</span></span><br /><br /> <span data-ttu-id="90c84-166">**儲存體**：儲存體已滿。</span><span class="sxs-lookup"><span data-stu-id="90c84-166">**Storage**: The storage is full.</span></span> <span data-ttu-id="90c84-167">當有額外的儲存體可用時，處理作業便會繼續。</span><span class="sxs-lookup"><span data-stu-id="90c84-167">Processing resumes when additional storage becomes available.</span></span><br /><br /> <span data-ttu-id="90c84-168">**記錄器**：記錄器連接到 Oracle，但由於暫時性問題無法讀取 Oracle 交易記錄，例如，無法使用必要的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="90c84-168">**Logger**: The logger is connected to Oracle but cannot read the Oracle transaction logs due to a temporary problem, for example, a required transaction log is not available.</span></span>|  
  
-   <span data-ttu-id="90c84-169">**詳細狀態**：目前的子狀態。</span><span class="sxs-lookup"><span data-stu-id="90c84-169">**Detailed Status**: The current substatus.</span></span>  
  
-   <span data-ttu-id="90c84-170">**狀態訊息**：有關目前狀態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-170">**Status Message**: More information about the current status.</span></span>  
  
-   <span data-ttu-id="90c84-171">**時間戳記**：上次從狀態資料表讀取 CDC 狀態時的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="90c84-171">**Timestamp**: The UTC time for when the CDC state was last read from the state table.</span></span>  
  
-   <span data-ttu-id="90c84-172">**目前正在處理**：您會在此區段中監視以下資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-172">**Currently Processing**: You monitor the following information in this section.</span></span>  
  
    -   <span data-ttu-id="90c84-173">**上次交易時間戳記**：上次交易寫入變更資料表時的當地時間。</span><span class="sxs-lookup"><span data-stu-id="90c84-173">**Last transaction timestamp**: The local time of the last transaction written to the change tables.</span></span>  
  
    -   <span data-ttu-id="90c84-174">**上次變更時間戳記**：來源 Oracle 資料庫交易記錄中的 Oracle CDC 執行個體查看最近變更時的當地時間。</span><span class="sxs-lookup"><span data-stu-id="90c84-174">**Last change timestamp**: The local time of the most recent change seen by the Oracle CDC Instance in the source Oracle database transaction logs.</span></span> <span data-ttu-id="90c84-175">這會提供有關 CDC 執行個體讀取 Oracle 交易記錄之目前延遲的資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-175">This provides information about the current latency of the CDC instance in reading the Oracle transaction log.</span></span>  
  
    -   <span data-ttu-id="90c84-176">**交易記錄標頭 CN**：從 Oracle 交易記錄讀取的最近變更編號 (CN)。</span><span class="sxs-lookup"><span data-stu-id="90c84-176">**Transaction log head CN**: The most recent change number (CN) that was read from the Oracle transaction log.</span></span>  
  
    -   <span data-ttu-id="90c84-177">**交易記錄結尾 CN**：復原或重新啟動 CDC 執行個體的變更編號。</span><span class="sxs-lookup"><span data-stu-id="90c84-177">**Transaction log tail CN**: The change number for recovery or restarting the CDC instance.</span></span> <span data-ttu-id="90c84-178">萬一重新啟動或發生任何其他類型的失敗 (包括叢集容錯移轉)，Oracle CDC 執行個體將會重新調整到這個位置。</span><span class="sxs-lookup"><span data-stu-id="90c84-178">The Oracle CDC instance will reposition to this location in the event of a re-start or any other type of failure (including cluster failover).</span></span>  
  
    -   <span data-ttu-id="90c84-179">**目前 CN**：來源 Oracle 資料庫 (不是交易記錄) 中看到的上次變更編號 (SCN)。</span><span class="sxs-lookup"><span data-stu-id="90c84-179">**Current CN**: The last change number (SCN) seen in the source Oracle database (not the transaction log).</span></span>  
  
    -   <span data-ttu-id="90c84-180">**使用中交易**：Oracle CDC 執行個體正在處理而且尚未決定 (認可/回復) 之來源 Oracle 交易的目前數目。</span><span class="sxs-lookup"><span data-stu-id="90c84-180">**Active transactions**: The current number of source Oracle transactions that are being processed by the Oracle CDC Instance and are not yet decided (commit/rollback).</span></span>  
  
    -   <span data-ttu-id="90c84-181">**暫存交易**：暫存至 [cdc.xdbcdc_staged_transactions](the-oracle-cdc-databases.md#bkmk_cdcxdbcdc_staged_transactions) 資料表之來源 Oracle 交易的目前數目。</span><span class="sxs-lookup"><span data-stu-id="90c84-181">**Staged transactions**: The current number source Oracle transactions that are staged to the [cdc.xdbcdc_staged_transactions](the-oracle-cdc-databases.md#bkmk_cdcxdbcdc_staged_transactions) table.</span></span>  
  
-   <span data-ttu-id="90c84-182">**計數器**：您會在此區段中監視以下資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-182">**Counters**: You monitor the following information in this section.</span></span>  
  
    -   <span data-ttu-id="90c84-183">**完成的交易**：上次重設 CDC 執行個體之後完成的交易數目。</span><span class="sxs-lookup"><span data-stu-id="90c84-183">**Completed transactions**: The number of transactions completed since the CDC instance was last reset.</span></span> <span data-ttu-id="90c84-184">這不包括未包含相關資料表的交易。</span><span class="sxs-lookup"><span data-stu-id="90c84-184">This does not include transactions that do not contain tables of interest.</span></span>  
  
    -   <span data-ttu-id="90c84-185">**寫入的變更**：寫入 SQL Server 變更資料表的變更數目。</span><span class="sxs-lookup"><span data-stu-id="90c84-185">**Written changes**: The number of changes written to the SQL Server change tables.</span></span>  
  
 <span data-ttu-id="90c84-186">**Oracle**</span><span class="sxs-lookup"><span data-stu-id="90c84-186">**Oracle**</span></span>  
 <span data-ttu-id="90c84-187">顯示有關 CDC 執行個體以及它與 Oracle 資料庫之連接的資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-187">Displays information about the CDC instance and its connection to the Oracle database.</span></span> <span data-ttu-id="90c84-188">此索引標籤是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="90c84-188">This tab is read only.</span></span> <span data-ttu-id="90c84-189">若要編輯這些屬性，請以滑鼠右鍵按一下左窗格中的執行個體，然後選取 [屬性] 或按一下右窗格中的 [屬性] 以開啟 [\<instance> 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="90c84-189">To edit these properties, right-click the instance in the left pane and select **Properties** or click **Properties** in the right pane to open the \<instance> Properties dialog box.</span></span>  
  
 <span data-ttu-id="90c84-190">如需有關這些屬性以及如何加以編輯的詳細資訊，請參閱＜ [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="90c84-190">For information about these properties and how to edit them, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
 <span data-ttu-id="90c84-191">**資料表**</span><span class="sxs-lookup"><span data-stu-id="90c84-191">**Tables**</span></span>  
 <span data-ttu-id="90c84-192">顯示有關 CDC 執行個體中包含之資料表的資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-192">Displays information about the tables included in the CDC instance.</span></span> <span data-ttu-id="90c84-193">這裡也會提供資料行資訊。</span><span class="sxs-lookup"><span data-stu-id="90c84-193">Column information is also available here.</span></span> <span data-ttu-id="90c84-194">此索引標籤是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="90c84-194">This tab is read only.</span></span> <span data-ttu-id="90c84-195">若要編輯這些屬性，請以滑鼠右鍵按一下左窗格中的執行個體，然後選取 [屬性] 或按一下右窗格中的 [屬性] 以開啟 [\<instance> 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="90c84-195">To edit these properties, right-click the instance in the left pane and select **Properties** or click **Properties** in the right pane to open the \<instance> Properties dialog box.</span></span>  
  
 <span data-ttu-id="90c84-196">如需有關這些屬性以及如何加以編輯的詳細資訊，請參閱＜ [Edit Tables](edit-tables.md)＞。</span><span class="sxs-lookup"><span data-stu-id="90c84-196">For information about these properties and how to edit them, see [Edit Tables](edit-tables.md).</span></span>  
  
 <span data-ttu-id="90c84-197">**進階**</span><span class="sxs-lookup"><span data-stu-id="90c84-197">**Advanced**</span></span>  
 <span data-ttu-id="90c84-198">顯示 CDC 執行個體的進階屬性和屬性值。</span><span class="sxs-lookup"><span data-stu-id="90c84-198">Displays the advanced properties for the CDC instance and the property values.</span></span> <span data-ttu-id="90c84-199">此索引標籤是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="90c84-199">This tab is read only.</span></span> <span data-ttu-id="90c84-200">若要編輯這些屬性，請以滑鼠右鍵按一下左窗格中的執行個體，然後選取 [屬性] 或按一下右窗格中的 [屬性] 以開啟 [\<instance> 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="90c84-200">To edit these properties, right-click the instance in the left pane and select **Properties** or click **Properties** in the right pane to open the \<instance> Properties dialog box.</span></span>  
  
 <span data-ttu-id="90c84-201">如需有關這些屬性以及如何加以編輯的詳細資訊，請參閱＜ [Edit the Advanced Properties](edit-the-advanced-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="90c84-201">For information about these properties and how to edit them, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c84-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90c84-202">See Also</span></span>  
 <span data-ttu-id="90c84-203">[如何建立 SQL Server 變更資料庫執行個體](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="90c84-203">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="90c84-204">[如何檢視 CDC 執行個體屬性](how-to-view-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="90c84-204">[How to View the CDC Instance Properties](how-to-view-the-cdc-instance-properties.md) </span></span>  
 <span data-ttu-id="90c84-205">[如何編輯 CDC 執行個體屬性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="90c84-205">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 <span data-ttu-id="90c84-206">[使用 [新增執行個體精靈]](use-the-new-instance-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="90c84-206">[Use the New Instance Wizard](use-the-new-instance-wizard.md)</span></span>  
