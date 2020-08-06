---
title: 設定叢集仲裁 NodeWeight 設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: cb3fd9a6-39a2-4e9c-9157-619bf3db9951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e469d5fc0fc030304a7cf2f1bdd894eb578aa056
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595573"
---
# <a name="configure-cluster-quorum-nodeweight-settings"></a><span data-ttu-id="223fb-102">設定叢集仲裁 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="223fb-102">Configure Cluster Quorum NodeWeight Settings</span></span>
  <span data-ttu-id="223fb-103">本主題說明如何設定 Windows Server 容錯移轉叢集 (WSFC) 叢集中成員節點的 NodeWeight 設定。</span><span class="sxs-lookup"><span data-stu-id="223fb-103">This topic describes how to configure NodeWeight settings for a member node in a Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="223fb-104">在仲裁投票期間，使用 NodeWeight 設定來支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的災害復原和多重子網路案例。</span><span class="sxs-lookup"><span data-stu-id="223fb-104">NodeWeight settings are used during quorum voting to support disaster recovery and multi-subnet scenarios for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="223fb-105">**開始之前：** [必要條件](#Prerequisites)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="223fb-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="223fb-106">**若要使用下列工具檢視仲裁 NodeWeight 設定：** [使用 PowerShell](#PowerShellProcedure)、[使用 Cluster.exe](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="223fb-106">**To view quorum NodeWeight settings using:** [Using Powershell](#PowerShellProcedure), [Using Cluster.exe](#CommandPromptProcedure)</span></span>  
  
-   [<span data-ttu-id="223fb-107">相關內容</span><span class="sxs-lookup"><span data-stu-id="223fb-107">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="223fb-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="223fb-108">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="223fb-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="223fb-109">Prerequisites</span></span>  
 <span data-ttu-id="223fb-110">只有 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 或更新版本才支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="223fb-110">This feature is supported only in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] or later versions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="223fb-111">為了能夠使用 NodeWeight 設定，必須將以下 Hotfix 套用至 WSFC 叢集中的所有伺服器：</span><span class="sxs-lookup"><span data-stu-id="223fb-111">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="223fb-112">[KB2494036](https://support.microsoft.com/kb/2494036)：提供 Hotfix 讓您設定叢集節點，該節點在 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 和 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 中沒有仲裁投票</span><span class="sxs-lookup"><span data-stu-id="223fb-112">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="223fb-113">如果未安裝此 Hotfix，本主題的範例會針對 NodeWeight 傳回空的值或 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="223fb-113">If this hotfix is not installed, the examples in this topic will return empty or NULL values for NodeWeight.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="223fb-114">Security</span><span class="sxs-lookup"><span data-stu-id="223fb-114">Security</span></span>  
 <span data-ttu-id="223fb-115">使用者必須是屬於 WSFC 叢集之每一個節點上本機 Administrators 群組成員的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="223fb-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="223fb-116">使用 Powershell</span><span class="sxs-lookup"><span data-stu-id="223fb-116">Using Powershell</span></span>  
  
### <a name="to-configure-nodeweight-settings"></a><span data-ttu-id="223fb-117">若要設定 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="223fb-117">To configure NodeWeight settings</span></span>
  
1.  <span data-ttu-id="223fb-118">透過 **[以系統管理員身分執行]** 來啟動更高權限的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="223fb-118">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="223fb-119">匯入 `FailoverClusters` 模組來啟用叢集指令程式。</span><span class="sxs-lookup"><span data-stu-id="223fb-119">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="223fb-120">使用 `Get-ClusterNode` 物件來設定叢集中每個節點的 `NodeWeight` 屬性。</span><span class="sxs-lookup"><span data-stu-id="223fb-120">Use the `Get-ClusterNode` object to set the `NodeWeight` property for each node in the cluster.</span></span>  
  
4.  <span data-ttu-id="223fb-121">以可讀格式輸出叢集節點屬性。</span><span class="sxs-lookup"><span data-stu-id="223fb-121">Output the cluster node properties in a readable format.</span></span>  
  
 <span data-ttu-id="223fb-122">下列範例會變更 NodeWeight 設定，以便移除 "AlwaysOnSrv1" 節點的仲裁投票，然後輸出叢集中所有節點的設定。</span><span class="sxs-lookup"><span data-stu-id="223fb-122">The following example changes the NodeWeight setting to remove the quorum vote for the "AlwaysOnSrv1" node, and then outputs the settings for all nodes in the cluster.</span></span>
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv1"  
(Get-ClusterNode $node).NodeWeight = 0  
  
$cluster = (Get-ClusterNode $node).Cluster  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="223fb-123">使用 Cluster.exe</span><span class="sxs-lookup"><span data-stu-id="223fb-123">Using Cluster.exe</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="223fb-124">cluster.exe 公用程式在 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 版本中已過時。</span><span class="sxs-lookup"><span data-stu-id="223fb-124">The cluster.exe utility is deprecated in the [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] release.</span></span>  <span data-ttu-id="223fb-125">在未來的開發中，請搭配容錯移轉叢集使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="223fb-125">Please use PowerShell with Failover Clustering for future development.</span></span>  <span data-ttu-id="223fb-126">下一版的 Windows Server 將會移除 cluster.exe 公用程式。</span><span class="sxs-lookup"><span data-stu-id="223fb-126">The cluster.exe utility will be removed in the next release of Windows Server.</span></span> <span data-ttu-id="223fb-127">如需詳細資訊，請參閱 [針對容錯移轉叢集將 Cluster.exe 命令對應到 Windows PowerShell 指令程式](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="223fb-127">For more information, see [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).</span></span>  
  
### <a name="to-configure-nodeweight-settings"></a><span data-ttu-id="223fb-128">若要設定 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="223fb-128">To configure NodeWeight settings</span></span>
  
1.  <span data-ttu-id="223fb-129">透過 **[以系統管理員身分執行]** 來啟動更高權限的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="223fb-129">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="223fb-130">使用 **cluster.exe** 設定 `NodeWeight` 值。</span><span class="sxs-lookup"><span data-stu-id="223fb-130">Use **cluster.exe** to set `NodeWeight` values.</span></span>  

 <span data-ttu-id="223fb-131">下列範例會變更 NodeWeight 值，以便在 "Cluster001" 叢集中移除 "AlwaysOnSrv1" 節點的仲裁投票。</span><span class="sxs-lookup"><span data-stu-id="223fb-131">The following example changes the NodeWeight value to remove the quorum vote of the "AlwaysOnSrv1" node in the "Cluster001" cluster.</span></span>  
  
```cmd
cluster.exe Cluster001 node AlwaysOnSrv1 /prop NodeWeight=0  
```  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="223fb-132">相關內容</span><span class="sxs-lookup"><span data-stu-id="223fb-132">Related Content</span></span>  
  
-   <span data-ttu-id="223fb-133">[檢視容錯移轉叢集的事件和記錄檔](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="223fb-133">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="223fb-134">Get-ClusterLog 容錯移轉叢集指令程式</span><span class="sxs-lookup"><span data-stu-id="223fb-134">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="223fb-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="223fb-135">See Also</span></span>  
 <span data-ttu-id="223fb-136">[WSFC 仲裁模式和投票設定 &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="223fb-136">[WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="223fb-137">[View Cluster 仲裁 NodeWeight 設定](view-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="223fb-137">[View Cluster Quorum NodeWeight Settings](view-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="223fb-138">[Windows PowerShell 中由工作焦點列出的容錯移轉叢集指令程式 ](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="223fb-138">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
