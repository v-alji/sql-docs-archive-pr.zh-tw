---
title: 可用性群組已離線 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp2online.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 093c5208-bf7a-49f4-a546-72b48197cadf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b25e5b22a09783c8dfcad862500b5c0dfcb2c319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585616"
---
# <a name="availability-group-is-offline"></a><span data-ttu-id="66cf7-102">可用性群組為離線</span><span class="sxs-lookup"><span data-stu-id="66cf7-102">Availability group is offline</span></span>
    
## <a name="introduction"></a><span data-ttu-id="66cf7-103">簡介</span><span class="sxs-lookup"><span data-stu-id="66cf7-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66cf7-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="66cf7-104">**Policy Name**</span></span>|<span data-ttu-id="66cf7-105">可用性群組線上狀態</span><span class="sxs-lookup"><span data-stu-id="66cf7-105">Availability Group Online State</span></span>|  
|<span data-ttu-id="66cf7-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="66cf7-106">**Issue**</span></span>|<span data-ttu-id="66cf7-107">可用性群組為離線。</span><span class="sxs-lookup"><span data-stu-id="66cf7-107">Availability group is offline.</span></span>|  
|<span data-ttu-id="66cf7-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="66cf7-108">**Category**</span></span>|<span data-ttu-id="66cf7-109">**嚴重**</span><span class="sxs-lookup"><span data-stu-id="66cf7-109">**Critical**</span></span>|  
|<span data-ttu-id="66cf7-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="66cf7-110">**Facet**</span></span>|<span data-ttu-id="66cf7-111">可用性群組</span><span class="sxs-lookup"><span data-stu-id="66cf7-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="66cf7-112">描述</span><span class="sxs-lookup"><span data-stu-id="66cf7-112">Description</span></span>  
 <span data-ttu-id="66cf7-113">這項原則檢查可用性群組的線上或離線狀態。</span><span class="sxs-lookup"><span data-stu-id="66cf7-113">This policy checks the online or offline state of the availability group.</span></span> <span data-ttu-id="66cf7-114">當可用性群組的叢集資源為離線或可用性群組沒有主要複本時，原則為狀況不良並會引發警示。</span><span class="sxs-lookup"><span data-stu-id="66cf7-114">The policy is in an unhealthy state and an alert is raised when the cluster resource of the availability group is offline or the availability group does not have a primary replica.</span></span>  
  
 <span data-ttu-id="66cf7-115">當可用性群組的叢集資源為線上或可用性群組有主要複本時，原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="66cf7-115">The policy state is healthy when the cluster resource of the availability group is online and the availability group has a primary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66cf7-116"> 在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [可用性群組為離線](https://go.microsoft.com/fwlink/p/?LinkId=220850) 。</span><span class="sxs-lookup"><span data-stu-id="66cf7-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability group is offline](https://go.microsoft.com/fwlink/p/?LinkId=220850) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="66cf7-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="66cf7-117">Possible Causes</span></span>  
 <span data-ttu-id="66cf7-118">這個問題可能是由於裝載主要複本的伺服器執行個體失敗或由於 Windows Server 容錯移轉叢集 (WSFC) 可用性群組資源離線所造成。</span><span class="sxs-lookup"><span data-stu-id="66cf7-118">This issue can be caused by a failure in the server instance that hosts the primary replica or by the Windows Server Failover Cluster (WSFC) availability group resource going offline.</span></span> <span data-ttu-id="66cf7-119">造成可用性群組離線的可能原因如下：</span><span class="sxs-lookup"><span data-stu-id="66cf7-119">Following are possible causes for the availability group to be offline:</span></span>  
  
-   <span data-ttu-id="66cf7-120">可用性群組未設定為自動容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="66cf7-120">The availability group is not configured with automatic failover mode.</span></span> <span data-ttu-id="66cf7-121">主要複本變為不可用，而且可用性群組中所有複本的角色變為 RESOLVING。</span><span class="sxs-lookup"><span data-stu-id="66cf7-121">The primary replica becomes unavailable and the role of all replicas in the availability group become RESOLVING.</span></span>  
  
    -   <span data-ttu-id="66cf7-122">主要複本執行個體服務已關閉或沒有回應。</span><span class="sxs-lookup"><span data-stu-id="66cf7-122">The primary replica instance service is down or unresponsive.</span></span>  
  
    -   <span data-ttu-id="66cf7-123">可用性群組與叢集之間發生連接問題。</span><span class="sxs-lookup"><span data-stu-id="66cf7-123">The availability group has a connectivity issue with the cluster.</span></span>  
  
-   <span data-ttu-id="66cf7-124">可用性群組設定為自動容錯移轉模式，但未成功完成。</span><span class="sxs-lookup"><span data-stu-id="66cf7-124">The availability group is configured with automatic failover mode and does not complete successfully.</span></span>  
  
    -   <span data-ttu-id="66cf7-125">在自動容錯移轉期間，目標複本的主要整備檢查失敗，但沒有複本可成為新的主要複本。</span><span class="sxs-lookup"><span data-stu-id="66cf7-125">During the automatic failover, the primary readiness check on the target replica fails, and there is no replica available to become the new primary.</span></span>  
  
-   <span data-ttu-id="66cf7-126">叢集中的可用性群組資源變成離線。</span><span class="sxs-lookup"><span data-stu-id="66cf7-126">The availability group resource in the cluster becomes offline.</span></span>  
  
    -   <span data-ttu-id="66cf7-127">任何相依叢集資源發生嚴重的問題，並成為離線。</span><span class="sxs-lookup"><span data-stu-id="66cf7-127">Any dependent cluster resource encounters a critical issue and becomes offline.</span></span> <span data-ttu-id="66cf7-128">可用性群組資源也處於離線狀態，直到相依的資源變為連線狀態。</span><span class="sxs-lookup"><span data-stu-id="66cf7-128">The availability group resource is also offline until the dependent resource becomes online.</span></span>  
  
    -   <span data-ttu-id="66cf7-129">叢集中的嚴重問題使可用性群組資源關閉。</span><span class="sxs-lookup"><span data-stu-id="66cf7-129">A critical issue in the cluster turns off the availability group resource.</span></span>  
  
-   <span data-ttu-id="66cf7-130">可用性群組正在進行自動、手動或強制的容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="66cf7-130">There is an automatic, manual, or forced failover in progress for the availability group.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="66cf7-131">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="66cf7-131">Possible Solutions</span></span>  
 <span data-ttu-id="66cf7-132">此問題的可能解決方案如下：</span><span class="sxs-lookup"><span data-stu-id="66cf7-132">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="66cf7-133">如果主要複本的 SQL Server 執行個體已關閉，請重新啟動伺服器，然後確認可用性群組是否復原為狀況良好的狀態。</span><span class="sxs-lookup"><span data-stu-id="66cf7-133">If the SQL Server instance of the primary replica is down, restart the server and then verify that the availability group recovers to a healthy state.</span></span>  
  
-   <span data-ttu-id="66cf7-134">如果自動容錯移轉似乎失敗，請確認複本上的資料庫是否與先前的主要複本同步處理，然後容錯移轉至主要複本。</span><span class="sxs-lookup"><span data-stu-id="66cf7-134">If the automatic failover appears to have failed, verify that the databases on the replica are synchronized with the previously known primary replica, and then failover to the primary replica.</span></span> <span data-ttu-id="66cf7-135">如果資料庫未同步處理，請選取資料遺失最少的複本，然後復原為容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="66cf7-135">If the databases are not synchronized, select a replica with a minimum loss of data, and then recover to failover mode.</span></span>  
  
-   <span data-ttu-id="66cf7-136">如果在 SQL Server 執行個體似乎狀況良好時，叢集中的資源離線，請使用容錯移轉叢集管理員檢查叢集健全狀況或伺服器上的其他叢集問題。</span><span class="sxs-lookup"><span data-stu-id="66cf7-136">If the resource in the cluster is offline while the instances of SQL Server appear to be healthy, use Failover Cluster Manager to check the cluster health or other cluster issues on the server.</span></span> <span data-ttu-id="66cf7-137">您還可以使用容錯移轉叢集管理員，嘗試將可用性群組資源恢復上線。</span><span class="sxs-lookup"><span data-stu-id="66cf7-137">You can also use the Failover Cluster Manager to attempt to turn the availability group resource online.</span></span>  
  
-   <span data-ttu-id="66cf7-138">如果正在進行容錯移轉，請等候容錯移轉完成。</span><span class="sxs-lookup"><span data-stu-id="66cf7-138">If there is a failover in progress, wait for the failover to complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66cf7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66cf7-139">See Also</span></span>  
 <span data-ttu-id="66cf7-140">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="66cf7-140">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="66cf7-141">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="66cf7-141">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
