---
title: 在無仲裁情況下強制啟動 WSFC 叢集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: 4a121375-7424-4444-b876-baefa8fe9015
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6f2110b706de015d0c7b19475b335908c118267
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595561"
---
# <a name="force-a-wsfc-cluster-to-start-without-a-quorum"></a><span data-ttu-id="6c4c5-102">在無仲裁情況下強制啟動 WSFC 叢集</span><span class="sxs-lookup"><span data-stu-id="6c4c5-102">Force a WSFC Cluster to Start Without a Quorum</span></span>
  <span data-ttu-id="6c4c5-103">本主題描述如何在沒有仲裁的情況下強制啟動 Windows Server 容錯移轉叢集 (WSFC) 叢集節點。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-103">This topic describes how to force a Windows Server Failover Clustering (WSFC) cluster node to start without a quorum.</span></span>  <span data-ttu-id="6c4c5-104">在災害復原和多重子網路案例中，可能需要這個方式才能針對 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體來復原資料及完整重新建立高可用性。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-104">This may be required in disaster recovery and multi-subnet scenarios to recover data and fully re-establish high-availability for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="6c4c5-105">**開始之前：**  [建議](#Recommendations)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="6c4c5-105">**Before you start:**  [Recommendations](#Recommendations), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="6c4c5-106">**使用下列項目在沒有仲裁的情況下強制啟動叢集︰**  [使用容錯移轉叢集管理員](#FailoverClusterManagerProcedure)、[使用 PowerShell](#PowerShellProcedure)、[使用 Net.exe](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="6c4c5-106">**To force a cluster to start without a quorum using:**  [Using Failover Cluster Manager](#FailoverClusterManagerProcedure), [Using Powershell](#PowerShellProcedure), [Using Net.exe](#CommandPromptProcedure)</span></span>  
  
-   <span data-ttu-id="6c4c5-107">**後續操作：**  [在沒有仲裁的情況下強制啟動叢集之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="6c4c5-107">**Follow up:**  [Follow Up: After Forcing Cluster to Start without a Quorum](#FollowUp)</span></span>  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6c4c5-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="6c4c5-108">Before You Start</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6c4c5-109">建議</span><span class="sxs-lookup"><span data-stu-id="6c4c5-109">Recommendations</span></span>  
 <span data-ttu-id="6c4c5-110">除了明確指示的內容以外，如果您從 WSFC 叢集中的任何節點執行本主題的程序，都應該有效。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-110">Except where explicitly directed, the procedures in this topic should work if you execute them from any node in the WSFC cluster.</span></span>  <span data-ttu-id="6c4c5-111">但是，如果您從打算在無仲裁情況下強制啟動的節點執行這些步驟，您可能會得到更好的結果並避免網路問題發生。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-111">However, you may obtain better results, and avoid networking issues, by executing these steps from the node that you intend to force to start without a quorum.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6c4c5-112">Security</span><span class="sxs-lookup"><span data-stu-id="6c4c5-112">Security</span></span>  
 <span data-ttu-id="6c4c5-113">使用者必須是屬於 WSFC 叢集之每一個節點上本機 Administrators 群組成員的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-113">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-failover-cluster-manager"></a><a name="FailoverClusterManagerProcedure"></a><span data-ttu-id="6c4c5-114">使用容錯移轉叢集管理員</span><span class="sxs-lookup"><span data-stu-id="6c4c5-114">Using Failover Cluster Manager</span></span>  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="6c4c5-115">若要在無仲裁情況下強制啟動叢集</span><span class="sxs-lookup"><span data-stu-id="6c4c5-115">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="6c4c5-116">開啟容錯移轉叢集管理員，並連接到所要的叢集節點來強制連線。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-116">Open a Failover Cluster Manager and connect to the desired cluster node to force online.</span></span>  
  
2.  <span data-ttu-id="6c4c5-117">在 [**動作**] 窗格中，按一下 [**強制**啟動叢集]，然後按一下 [**是-強制啟動我的叢集]**。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-117">In the **Actions** pane, click **Force Cluster Start**, and then click **Yes - Force my cluster to start**.</span></span>  
  
3.  <span data-ttu-id="6c4c5-118">在左窗格的 **[容錯移轉叢集管理員]** 樹狀目錄中，按一下叢集名稱。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-118">In the left pane, in the **Failover Cluster Manager** tree, click the cluster name.</span></span>  
  
4.  <span data-ttu-id="6c4c5-119">在摘要窗格中，確認目前 **[仲裁設定]** 值為  **[警告: 叢集正在以 ForceQuorum 狀態執行]**。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-119">In the summary pane, confirm that the current **Quorum Configuration** value is:  **Warning: Cluster is running in ForceQuorum state**.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="6c4c5-120">使用 Powershell</span><span class="sxs-lookup"><span data-stu-id="6c4c5-120">Using Powershell</span></span>  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="6c4c5-121">若要在無仲裁情況下強制啟動叢集</span><span class="sxs-lookup"><span data-stu-id="6c4c5-121">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="6c4c5-122">透過 **[以系統管理員身分執行]** 來啟動更高權限的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-122">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="6c4c5-123">匯入 `FailoverClusters` 模組來啟用叢集指令程式。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-123">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="6c4c5-124">使用 `Stop-ClusterNode` 來確定叢集服務已停止。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-124">Use `Stop-ClusterNode` to make sure that the cluster service is stopped.</span></span>  
  
4.  <span data-ttu-id="6c4c5-125">搭配 `Start-ClusterNode` 使用 `-FixQuorum` 來強制啟動叢集服務。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-125">Use `Start-ClusterNode` with `-FixQuorum` to force the cluster service to start.</span></span>  
  
5.  <span data-ttu-id="6c4c5-126">搭配 `Get-ClusterNode` 使用 `-Propery NodeWieght = 1` 來設定值，該值保證節點為仲裁的投票成員。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-126">Use `Get-ClusterNode` with `-Propery NodeWieght = 1` to set the value the guarantees that the node is a voting member of the quorum.</span></span>  
  
6.  <span data-ttu-id="6c4c5-127">以可讀格式輸出叢集節點屬性。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-127">Output the cluster node properties in a readable format.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="6c4c5-128">範例 (Powershell)</span><span class="sxs-lookup"><span data-stu-id="6c4c5-128">Example (Powershell)</span></span>  
 <span data-ttu-id="6c4c5-129">下列範例會在沒有仲裁情況下強制啟動 AlwaysOnSrv02 節點叢集服務、設定 `NodeWeight = 1`，然後從新強制的節點列舉叢集節點狀態。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-129">The following example forces the AlwaysOnSrv02 node cluster service to start without a quorum, sets the `NodeWeight = 1`, and then enumerates cluster node status from the newly forced node.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv02"  
Stop-ClusterNode -Name $node  
Start-ClusterNode -Name $node -FixQuorum  
  
(Get-ClusterNode $node).NodeWeight = 1  
  
$nodes = Get-ClusterNode -Cluster $node  
$nodes | Format-Table -property NodeName, State, NodeWeight
```  
  
##  <a name="using-netexe"></a><a name="CommandPromptProcedure"></a><span data-ttu-id="6c4c5-130">使用 Net.exe</span><span class="sxs-lookup"><span data-stu-id="6c4c5-130">Using Net.exe</span></span>  
  
### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="6c4c5-131">若要在無仲裁情況下強制啟動叢集</span><span class="sxs-lookup"><span data-stu-id="6c4c5-131">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="6c4c5-132">使用遠端桌面連接到所需的叢集節點，以強制連線。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-132">Use Remote Desktop to connect to the desired cluster node to force online.</span></span>  
  
2.  <span data-ttu-id="6c4c5-133">透過 **[以系統管理員身分執行]** 來啟動更高權限的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-133">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
3.  <span data-ttu-id="6c4c5-134">使用 **net.exe** 來確定本機叢集服務已停止。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-134">Use **net.exe** to make sure that the local cluster service is stopped.</span></span>  
  
4.  <span data-ttu-id="6c4c5-135">搭配 **使用** net.exe `/forcequorum` 來強制啟動本機叢集服務。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-135">Use **net.exe** with `/forcequorum` to force the local cluster service to start.</span></span>  
  
### <a name="example-netexe"></a><span data-ttu-id="6c4c5-136">範例 (Net.exe)</span><span class="sxs-lookup"><span data-stu-id="6c4c5-136">Example (Net.exe)</span></span>  
 <span data-ttu-id="6c4c5-137">下列範例會在沒有仲裁情況下強制啟動節點叢集服務、設定 `NodeWeight = 1`，然後從新強制的節點列舉叢集節點狀態。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-137">The following example forces a node cluster service to start without a quorum, sets the `NodeWeight = 1`, and then enumerates cluster node status from the newly forced node.</span></span>  
  
```cmd
net.exe stop clussvc  
net.exe start clussvc /forcequorum  
```  
  
##  <a name="follow-up-after-forcing-cluster-to-start-without-a-quorum"></a><a name="FollowUp"></a><span data-ttu-id="6c4c5-138">後續操作：在沒有仲裁的情況下強制啟動叢集之後</span><span class="sxs-lookup"><span data-stu-id="6c4c5-138">Follow Up: After Forcing Cluster to Start without a Quorum</span></span>  
  
-   <span data-ttu-id="6c4c5-139">在讓其他節點重新於線上工作之前，您必須重新評估及重新設定 NodeWeight 值，以正確建構新的仲裁。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-139">You must re-evaluate and reconfigure NodeWeight values to correctly construct a new quorum before bringing other nodes back online.</span></span> <span data-ttu-id="6c4c5-140">否則，叢集可能會再次離線。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-140">Otherwise, the cluster may go back offline again.</span></span>  
  
     <span data-ttu-id="6c4c5-141">如需詳細資訊，請參閱 [WSFC 仲裁模式和投票組態 &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-141">For more information, see [WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6c4c5-142">本主題的程序是在發生意外的仲裁失敗時，讓 WSFC 叢集重新於線上工作的唯一步驟。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-142">The procedures in this topic are only one step in bringing the WSFC cluster back online if an un-planned quorum failure were to occur.</span></span>  <span data-ttu-id="6c4c5-143">您可能也會想要採取額外步驟來阻止其他 WSFC 叢集節點干擾新的仲裁設定。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-143">You may also want to take additional steps to prevent other WSFC cluster nodes from interfering with the new quorum configuration.</span></span>  
  
-   <span data-ttu-id="6c4c5-144">其他 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能 (例如 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]、資料庫鏡像和記錄傳送) 可能也需要執行後續動作來復原資料及完整重建高可用性。</span><span class="sxs-lookup"><span data-stu-id="6c4c5-144">Other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features such as [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], database mirroring, and log shipping may also require subsequent actions to recover data and to fully re-establish high-availability.</span></span>  
  
     <span data-ttu-id="6c4c5-145">**如需詳細資訊：**</span><span class="sxs-lookup"><span data-stu-id="6c4c5-145">**For more information:**</span></span>  
  
     [<span data-ttu-id="6c4c5-146">執行可用性群組的強制手動容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6c4c5-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
     [<span data-ttu-id="6c4c5-147">在資料庫鏡像工作階段中強制服務 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c4c5-147">Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](../../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
  
     [<span data-ttu-id="6c4c5-148">容錯移轉至記錄傳送次要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6c4c5-148">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="6c4c5-149">相關內容</span><span class="sxs-lookup"><span data-stu-id="6c4c5-149">Related Content</span></span>  
  
-   <span data-ttu-id="6c4c5-150">[檢視容錯移轉叢集的事件和記錄檔](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="6c4c5-150">[View Events and Logs for a Failover Cluster](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))</span></span>  
  
-   [<span data-ttu-id="6c4c5-151">Get-ClusterLog 容錯移轉叢集指令程式</span><span class="sxs-lookup"><span data-stu-id="6c4c5-151">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="6c4c5-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c4c5-152">See Also</span></span>  
 <span data-ttu-id="6c4c5-153">[透過強制仲裁 &#40;SQL Server 的 WSFC 損毀修復&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6c4c5-153">[WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span></span>  
 <span data-ttu-id="6c4c5-154">[設定叢集仲裁 NodeWeight 設定](configure-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="6c4c5-154">[Configure Cluster Quorum NodeWeight Settings](configure-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="6c4c5-155">[Windows PowerShell 中由工作焦點列出的容錯移轉叢集指令程式 ](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="6c4c5-155">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
