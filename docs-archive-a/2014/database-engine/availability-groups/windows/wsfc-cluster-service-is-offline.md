---
title: WSFC 叢集服務已離線 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6e7b48f96eb09638291b1d0655d385d606b1666
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701905"
---
# <a name="wsfc-cluster-service-is-offline"></a><span data-ttu-id="94d08-102">WSFC 叢集服務離線</span><span class="sxs-lookup"><span data-stu-id="94d08-102">WSFC cluster service is offline</span></span>
    
## <a name="introduction"></a><span data-ttu-id="94d08-103">簡介</span><span class="sxs-lookup"><span data-stu-id="94d08-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94d08-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="94d08-104">**Policy Name**</span></span>|<span data-ttu-id="94d08-105">WSFC 叢集狀態</span><span class="sxs-lookup"><span data-stu-id="94d08-105">WSFC Cluster State</span></span>|  
|<span data-ttu-id="94d08-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="94d08-106">**Issue**</span></span>|<span data-ttu-id="94d08-107">WSFC 叢集服務已離線。</span><span class="sxs-lookup"><span data-stu-id="94d08-107">WSFC cluster service is offline.</span></span>|  
|<span data-ttu-id="94d08-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="94d08-108">**Category**</span></span>|<span data-ttu-id="94d08-109">**嚴重**</span><span class="sxs-lookup"><span data-stu-id="94d08-109">**Critical**</span></span>|  
|<span data-ttu-id="94d08-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="94d08-110">**Facet**</span></span>|<span data-ttu-id="94d08-111">SQL Server 的執行個體</span><span class="sxs-lookup"><span data-stu-id="94d08-111">Instance of SQL Server</span></span>|  
  
## <a name="description"></a><span data-ttu-id="94d08-112">描述</span><span class="sxs-lookup"><span data-stu-id="94d08-112">Description</span></span>  
 <span data-ttu-id="94d08-113">這項原則檢查 Windows Server 容錯移轉叢集 (WSFC) 的狀態。</span><span class="sxs-lookup"><span data-stu-id="94d08-113">This policy checks the state of the Windows Server Failover Cluster (WSFC).</span></span> <span data-ttu-id="94d08-114">當 WSFC 叢集已離線或處於強制仲裁狀態時，原則為狀況不良並會引發警示。</span><span class="sxs-lookup"><span data-stu-id="94d08-114">The policy is in an unhealthy state and an alert is raised when the WSFC cluster is offline or in the forced quorum state.</span></span> <span data-ttu-id="94d08-115">此叢集中裝載的所有可用性群組都已離線或需要災害復原動作。</span><span class="sxs-lookup"><span data-stu-id="94d08-115">All availability groups hosted within this cluster are offline or a disaster recovery action is required.</span></span>  
  
 <span data-ttu-id="94d08-116">當叢集狀態為標準仲裁時，原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="94d08-116">The policy state is healthy when the cluster state is in the normal quorum.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94d08-117">在此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [WSFC 叢集服務已離線](https://go.microsoft.com/fwlink/p/?LinkId=220849) 。</span><span class="sxs-lookup"><span data-stu-id="94d08-117">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [WSFC cluster service is offline](https://go.microsoft.com/fwlink/p/?LinkId=220849) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="94d08-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="94d08-118">Possible Causes</span></span>  
 <span data-ttu-id="94d08-119">這個問題可能是叢集服務問題或叢集遺失仲裁所造成。</span><span class="sxs-lookup"><span data-stu-id="94d08-119">This issue can be caused by a cluster service issue or by the loss of the quorum in the cluster.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="94d08-120">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="94d08-120">Possible Solution</span></span>  
 <span data-ttu-id="94d08-121">使用叢集管理員工具來執行強制仲裁或災害復原工作流程。</span><span class="sxs-lookup"><span data-stu-id="94d08-121">Use the Cluster Administrator tool to perform the forced quorum or disaster recovery workflow.</span></span> <span data-ttu-id="94d08-122">如果您無法透過執行強制仲裁或災害復原來解決問題，請向您的叢集管理員尋求協助。</span><span class="sxs-lookup"><span data-stu-id="94d08-122">If you cannot resolve the issue by performing the forced quorum or disaster recovery, contact your cluster administrator to help resolve this issue.</span></span> <span data-ttu-id="94d08-123">如需詳細資訊，請參閱《 [線上叢書》中的](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) 在無仲裁情況下強制啟動 WSFC 叢集 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="94d08-123">For more information, see [Force a WSFC Cluster to Start Without a Quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d08-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94d08-124">See Also</span></span>  
 <span data-ttu-id="94d08-125">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="94d08-125">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="94d08-126">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="94d08-126">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
