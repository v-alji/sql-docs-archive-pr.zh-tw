---
title: 檢視叢集仲裁 NodeWeight 設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: b845e73a-bb01-4de2-aac2-8ac12abebc95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef2176d4916e8affbb9ef89c9b26499289c520ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595558"
---
# <a name="view-cluster-quorum-nodeweight-settings"></a><span data-ttu-id="4cd77-102">檢視叢集仲裁 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="4cd77-102">View Cluster Quorum NodeWeight Settings</span></span>
  <span data-ttu-id="4cd77-103">本主題說明如何檢視 Windows Server 容錯移轉叢集 (WSFC) 叢集中每個成員節點的 NodeWeight 設定。</span><span class="sxs-lookup"><span data-stu-id="4cd77-103">This topic describes how to view NodeWeight settings for each member node in a Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="4cd77-104">在仲裁投票期間，使用 NodeWeight 設定來支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的災害復原和多重子網路案例。</span><span class="sxs-lookup"><span data-stu-id="4cd77-104">NodeWeight settings are used during quorum voting to support disaster recovery and multi-subnet scenarios for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="4cd77-105">**開始之前：** [必要條件](#Prerequisites)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="4cd77-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="4cd77-106">**若要使用下列工具檢視仲裁 NodeWeight 設定：** [使用 Transact-SQL](#TsqlProcedure)、[使用 Powershell](#PowerShellProcedure)、[使用 Cluster.exe](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="4cd77-106">**To view quorum NodeWeight settings using:** [Using Transact-SQL](#TsqlProcedure), [Using Powershell](#PowerShellProcedure), [Using Cluster.exe](#CommandPromptProcedure)</span></span>  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4cd77-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="4cd77-107">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="4cd77-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="4cd77-108">Prerequisites</span></span>  
 <span data-ttu-id="4cd77-109">只有 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 或更新版本才支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="4cd77-109">This feature is supported only in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] or later versions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4cd77-110">為了能夠使用 NodeWeight 設定，必須將以下 Hotfix 套用至 WSFC 叢集中的所有伺服器：</span><span class="sxs-lookup"><span data-stu-id="4cd77-110">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="4cd77-111">[KB2494036](https://support.microsoft.com/kb/2494036)：提供 Hotfix 讓您設定叢集節點，該節點在 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 和 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 中沒有仲裁投票</span><span class="sxs-lookup"><span data-stu-id="4cd77-111">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="4cd77-112">如果未安裝此 Hotfix，本主題的範例會針對 NodeWeight 傳回空的值或 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="4cd77-112">If this hotfix is not installed, the examples in this topic will return empty or NULL values for NodeWeight.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4cd77-113">Security</span><span class="sxs-lookup"><span data-stu-id="4cd77-113">Security</span></span>  
 <span data-ttu-id="4cd77-114">使用者必須是屬於 WSFC 叢集之每一個節點上本機 Administrators 群組成員的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="4cd77-114">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4cd77-115">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4cd77-115">Using Transact-SQL</span></span>  
  
##### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="4cd77-116">若要檢視 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="4cd77-116">To view NodeWeight settings</span></span>  
  
1.  <span data-ttu-id="4cd77-117">連接到叢集中的任何 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4cd77-117">Connect to any [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the cluster.</span></span>  
  
2.  <span data-ttu-id="4cd77-118">查詢 [sys].[dm_hadr_cluster_members] 檢視表。</span><span class="sxs-lookup"><span data-stu-id="4cd77-118">Query the [sys].[dm_hadr_cluster_members] view.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="4cd77-119">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4cd77-119">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4cd77-120">下列範例會查詢系統檢視表，以便針對該執行個體叢集中的所有節點傳回值。</span><span class="sxs-lookup"><span data-stu-id="4cd77-120">The following example queries a system view to return values for all of the nodes in that instance's cluster.</span></span>  
  
```sql  
SELECT  member_name, member_state_desc, number_of_quorum_votes  
 FROM   sys.dm_hadr_cluster_members;  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="4cd77-121">使用 Powershell</span><span class="sxs-lookup"><span data-stu-id="4cd77-121">Using Powershell</span></span>  
  
### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="4cd77-122">若要檢視 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="4cd77-122">To view NodeWeight settings</span></span>
  
1.  <span data-ttu-id="4cd77-123">透過 **[以系統管理員身分執行]** 來啟動更高權限的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4cd77-123">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="4cd77-124">匯入 `FailoverClusters` 模組來啟用叢集指令程式。</span><span class="sxs-lookup"><span data-stu-id="4cd77-124">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="4cd77-125">使用 `Get-ClusterNode` 物件來傳回叢集節點物件的集合。</span><span class="sxs-lookup"><span data-stu-id="4cd77-125">Use the `Get-ClusterNode` object to return a collection of cluster node objects.</span></span>  
  
4.  <span data-ttu-id="4cd77-126">以可讀格式輸出叢集節點屬性。</span><span class="sxs-lookup"><span data-stu-id="4cd77-126">Output the cluster node properties in a readable format.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="4cd77-127">範例 (Powershell)</span><span class="sxs-lookup"><span data-stu-id="4cd77-127">Example (Powershell)</span></span>  
 <span data-ttu-id="4cd77-128">下列範例會針對稱為 "Cluster001" 的叢集輸出某些節點屬性。</span><span class="sxs-lookup"><span data-stu-id="4cd77-128">The following example output some of the node properties for the cluster called "Cluster001".</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$cluster = "Cluster001"  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -Property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="4cd77-129">使用 Cluster.exe</span><span class="sxs-lookup"><span data-stu-id="4cd77-129">Using Cluster.exe</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cd77-130">cluster.exe 公用程式在 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 版本中已過時。</span><span class="sxs-lookup"><span data-stu-id="4cd77-130">The cluster.exe utility is deprecated in the [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] release.</span></span>  <span data-ttu-id="4cd77-131">在未來的開發中，請搭配容錯移轉叢集使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4cd77-131">Please use PowerShell with Failover Clustering for future development.</span></span>  <span data-ttu-id="4cd77-132">下一版的 Windows Server 將會移除 cluster.exe 公用程式。</span><span class="sxs-lookup"><span data-stu-id="4cd77-132">The cluster.exe utility will be removed in the next release of Windows Server.</span></span> <span data-ttu-id="4cd77-133">如需詳細資訊，請參閱 [針對容錯移轉叢集將 Cluster.exe 命令對應到 Windows PowerShell 指令程式](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="4cd77-133">For more information, see [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).</span></span>  
  
##### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="4cd77-134">若要檢視 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="4cd77-134">To view NodeWeight settings</span></span>  
  
1.  <span data-ttu-id="4cd77-135">透過 **[以系統管理員身分執行]** 來啟動更高權限的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="4cd77-135">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="4cd77-136">使用 **cluster.exe** 傳回節點狀態和 NodeWeight 值</span><span class="sxs-lookup"><span data-stu-id="4cd77-136">Use **cluster.exe** to return node status and NodeWeight values</span></span>  
  
### <a name="example-clusterexe"></a><span data-ttu-id="4cd77-137">範例 (Cluster.exe)</span><span class="sxs-lookup"><span data-stu-id="4cd77-137">Example (Cluster.exe)</span></span>  
 <span data-ttu-id="4cd77-138">下列範例會針對稱為 "Cluster001" 的叢集輸出某些節點屬性。</span><span class="sxs-lookup"><span data-stu-id="4cd77-138">The following example outputs some of the node properties for the cluster called "Cluster001".</span></span>  
  
```cmd
cluster.exe Cluster001 node /status /properties  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cd77-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cd77-139">See Also</span></span>  
 <span data-ttu-id="4cd77-140">[WSFC 仲裁模式和投票組態 &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4cd77-140">[WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="4cd77-141">[設定叢集仲裁 NodeWeight 設定](configure-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="4cd77-141">[Configure Cluster Quorum NodeWeight Settings](configure-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="4cd77-142">[sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4cd77-142">[sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql) </span></span>  
 <span data-ttu-id="4cd77-143">[Windows PowerShell 中由工作焦點列出的容錯移轉叢集指令程式](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="4cd77-143">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
