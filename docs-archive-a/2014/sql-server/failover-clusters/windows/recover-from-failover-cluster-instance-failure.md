---
title: 從容錯移轉叢集執行個體失敗的狀況復原 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], recovery from failure
- failover clustering [SQL Server], recovery from failure
- hardware failures [SQL Server]
- recovering failover cluster failures [SQL Server]
ms.assetid: 3d151d0c-e841-4325-8606-c094de37d7d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60db4c2e480b094c18d0a8071e947a38cdc779d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708113"
---
# <a name="recover-from-failover-cluster-instance-failure"></a><span data-ttu-id="1879d-102">從容錯移轉叢集執行個體失敗的狀況復原</span><span class="sxs-lookup"><span data-stu-id="1879d-102">Recover from Failover Cluster Instance Failure</span></span>
  <span data-ttu-id="1879d-103">此主題描述在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]發生容錯移轉之後，如何使用容錯移轉叢集管理員嵌入式管理單元，從叢集失敗中復原。</span><span class="sxs-lookup"><span data-stu-id="1879d-103">This topic describes how to recover from cluster failures by using the Failover Cluster Manager snap-in after a failover occurs in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1879d-104">容錯移轉叢集管理員嵌入式管理單元是 Windows Server 容錯移轉叢集 (WSFC) 服務的叢集管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="1879d-104">The Failover Cluster Manager snap-in is the cluster management application for the Windows Serer Failover Clustering (WSFC) service.</span></span>  
  
-   [<span data-ttu-id="1879d-105">從無法修復的失敗中復原</span><span class="sxs-lookup"><span data-stu-id="1879d-105">Recover from an irreparable failure</span></span>](#Scenario1)  
  
-   [<span data-ttu-id="1879d-106">從軟體失敗中復原</span><span class="sxs-lookup"><span data-stu-id="1879d-106">Recover from a software failure</span></span>](#Scenario2)  
  
##  <a name="recover-from-an-irreparable-failure"></a><a name="Scenario1"></a> <span data-ttu-id="1879d-107">從無法修復的失敗中復原</span><span class="sxs-lookup"><span data-stu-id="1879d-107">Recover from an irreparable failure</span></span>  
 <span data-ttu-id="1879d-108">您可以使用下列步驟從無法修復的失敗中復原。</span><span class="sxs-lookup"><span data-stu-id="1879d-108">Use the following steps to recover from an irreparable failure.</span></span> <span data-ttu-id="1879d-109">舉例來說，這種失敗可能是磁碟控制卡或作業系統失敗所引起。</span><span class="sxs-lookup"><span data-stu-id="1879d-109">The failure could be caused, for example, by the failure of a disk controller or the operating system.</span></span> <span data-ttu-id="1879d-110">在此情況下，失敗是兩節點叢集之節點 1 中的硬體故障所造成。</span><span class="sxs-lookup"><span data-stu-id="1879d-110">In this case, failure is caused by hardware failure in Node 1 of a two-node cluster.</span></span>  
  
1.  <span data-ttu-id="1879d-111">在節點 1 失敗之後， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI 會容錯移轉至節點 2。</span><span class="sxs-lookup"><span data-stu-id="1879d-111">After Node 1 fails, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI fails over to Node 2.</span></span>  
  
2.  <span data-ttu-id="1879d-112">從 FCI 中收回節點 1。</span><span class="sxs-lookup"><span data-stu-id="1879d-112">Evict Node 1 from the FCI.</span></span> <span data-ttu-id="1879d-113">作法是從節點 2 開啟容錯移轉叢集管理員嵌入式管理單元，並以滑鼠右鍵按一下 [節點 1]，按一下 [移動動作]\*\*\*\*，然後按一下 [收回節點]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1879d-113">To do this, from Node 2, open the Failover Cluster Manager snap-in, right-click Node1, click **Move Actions**, and then click **Evict Node**.</span></span>  
  
3.  <span data-ttu-id="1879d-114">確認節點 1 已從叢集定義中移出。</span><span class="sxs-lookup"><span data-stu-id="1879d-114">Verify that Node 1 has been evicted from the cluster definition.</span></span>  
  
4.  <span data-ttu-id="1879d-115">安裝新硬體來取代節點 1 中發生錯誤的硬體。</span><span class="sxs-lookup"><span data-stu-id="1879d-115">Install new hardware to replace the failed hardware in Node 1.</span></span>  
  
5.  <span data-ttu-id="1879d-116">使用容錯移轉叢集管理員嵌入式管理單元，將節點 1 加入至現有叢集。</span><span class="sxs-lookup"><span data-stu-id="1879d-116">Using the Failover Cluster Manager snap-in, add Node 1 to the existing cluster.</span></span> <span data-ttu-id="1879d-117">如需詳細資訊，請參閱 [安裝容錯移轉叢集之前](../install/before-installing-failover-clustering.md)。</span><span class="sxs-lookup"><span data-stu-id="1879d-117">For more information, see [Before Installing Failover Clustering](../install/before-installing-failover-clustering.md).</span></span>  
  
6.  <span data-ttu-id="1879d-118">確定所有叢集節點上的所有系統管理員帳戶都相同。</span><span class="sxs-lookup"><span data-stu-id="1879d-118">Ensure that the administrator accounts are the same on all cluster nodes.</span></span>  
  
7.  <span data-ttu-id="1879d-119">執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式，將節點 1 加入至 FCI。</span><span class="sxs-lookup"><span data-stu-id="1879d-119">Run [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup to add Node 1 to the FCI.</span></span> <span data-ttu-id="1879d-120">如需詳細資訊，請參閱[在 SQL Server 容錯移轉叢集中新增或移除節點 &#40;安裝程式&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="1879d-120">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
##  <a name="recover-from-a-reparable-failure"></a><a name="Scenario2"></a> <span data-ttu-id="1879d-121">從可修復的失敗中復原</span><span class="sxs-lookup"><span data-stu-id="1879d-121">Recover from a reparable failure</span></span>  
 <span data-ttu-id="1879d-122">您可以使用下列步驟從可修復的失敗中復原。</span><span class="sxs-lookup"><span data-stu-id="1879d-122">Us the following steps to recover from a reparable failure.</span></span> <span data-ttu-id="1879d-123">在此情況下，錯誤是節點 1 當機或離線所造成，但並非無可挽回的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="1879d-123">In this case, failure is caused by Node 1 being down or offline but not irretrievably broken.</span></span> <span data-ttu-id="1879d-124">這種失敗可能是因為作業系統失敗、硬體故障或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體本身失敗所導致。</span><span class="sxs-lookup"><span data-stu-id="1879d-124">This could be caused by an operating system failure, hardware failure, or failure in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance itself.</span></span>  
  
1.  <span data-ttu-id="1879d-125">在節點 1 失敗之後，FCI 會容錯移轉至節點 2。</span><span class="sxs-lookup"><span data-stu-id="1879d-125">After Node 1 fails, the FCI fails over to Node 2.</span></span>  
  
2.  <span data-ttu-id="1879d-126">解決節點 1 產生的問題。</span><span class="sxs-lookup"><span data-stu-id="1879d-126">Resolve the problem with Node 1.</span></span>  
  
3.  <span data-ttu-id="1879d-127">確定所有節點都在線上，而且 WSFC 服務正在運作。</span><span class="sxs-lookup"><span data-stu-id="1879d-127">Ensure that all nodes are online and the WSFC service is working.</span></span>  
  
4.  <span data-ttu-id="1879d-128">將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉至復原的節點。</span><span class="sxs-lookup"><span data-stu-id="1879d-128">Fail over [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the recovered node.</span></span>  
  
  
