---
title: 可用性群組尚未準備進行自動容錯移轉 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2995ddec51cd70d8a3f209229d0ecb9b0132c79e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585619"
---
# <a name="availability-group-is-not-ready-for-automatic-failover"></a><span data-ttu-id="5fba0-102">可用性群組尚未就緒，無法自動容錯</span><span class="sxs-lookup"><span data-stu-id="5fba0-102">Availability group is not ready for automatic failover</span></span>
    
## <a name="introduction"></a><span data-ttu-id="5fba0-103">簡介</span><span class="sxs-lookup"><span data-stu-id="5fba0-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fba0-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="5fba0-104">**Policy Name**</span></span>|<span data-ttu-id="5fba0-105">可用性群組自動容錯移轉整備</span><span class="sxs-lookup"><span data-stu-id="5fba0-105">Availability Group Automatic Failover Readiness</span></span>|  
|<span data-ttu-id="5fba0-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="5fba0-106">**Issue**</span></span>|<span data-ttu-id="5fba0-107">可用性群組尚未準備進行自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="5fba0-107">Availability group is not ready for automatic failover.</span></span>|  
|<span data-ttu-id="5fba0-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="5fba0-108">**Category**</span></span>|<span data-ttu-id="5fba0-109">**嚴重**</span><span class="sxs-lookup"><span data-stu-id="5fba0-109">**Critical**</span></span>|  
|<span data-ttu-id="5fba0-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="5fba0-110">**Facet**</span></span>|<span data-ttu-id="5fba0-111">可用性群組</span><span class="sxs-lookup"><span data-stu-id="5fba0-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5fba0-112">描述</span><span class="sxs-lookup"><span data-stu-id="5fba0-112">Description</span></span>  
 <span data-ttu-id="5fba0-113">這項原則檢查可用性群組是否至少有一個已做好容錯移轉準備的次要複本。</span><span class="sxs-lookup"><span data-stu-id="5fba0-113">This policy checks to verify that the availability group has at least one secondary replica that is failover ready.</span></span> <span data-ttu-id="5fba0-114">當主要複本的容錯移轉模式為自動，但是可用性群組中的次要複本都未準備進行容錯移轉時，原則為狀況不良並會引發警示。</span><span class="sxs-lookup"><span data-stu-id="5fba0-114">The policy is in an unhealthy state and an alert is raised when the failover mode of the primary replica is automatic, however none of the secondary replicas in the availability group are failover ready.</span></span>  
  
 <span data-ttu-id="5fba0-115">至少一個次要複本已做好自動容錯移轉的準備時，原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="5fba0-115">The policy is in a healthy state when at least one secondary replica is automatic failover ready.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fba0-116">在此 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]版本中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [Availability group is not ready for automatic failover](https://go.microsoft.com/fwlink/p/?LinkId=220851) (可用性群組尚未準備進行自動容錯移轉)。</span><span class="sxs-lookup"><span data-stu-id="5fba0-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability group is not ready for automatic failover](https://go.microsoft.com/fwlink/p/?LinkId=220851) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="5fba0-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="5fba0-117">Possible Causes</span></span>  
 <span data-ttu-id="5fba0-118">可用性群組尚未準備進行自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="5fba0-118">The availability group is not ready for automatic failover.</span></span> <span data-ttu-id="5fba0-119">主要複本已設定為自動容錯移轉，不過次要複本尚未準備進行自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="5fba0-119">The primary replica is configured for automatic failover; however, the secondary replica is not ready for automatic failover.</span></span> <span data-ttu-id="5fba0-120">設定為自動容錯移轉的次要複本可能無法使用，或者其資料同步處理狀態目前不是 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="5fba0-120">The secondary replica that is configured for automatic failover might be unavailable or its data synchronization state is currently not SYNCHRONIZED.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="5fba0-121">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="5fba0-121">Possible Solutions</span></span>  
 <span data-ttu-id="5fba0-122">此問題的可能解決方案如下：</span><span class="sxs-lookup"><span data-stu-id="5fba0-122">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="5fba0-123">請確認至少一個次要複本已設定為自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="5fba0-123">Verify that at least one secondary replica is configured as automatic failover.</span></span> <span data-ttu-id="5fba0-124">如果沒有設定為自動容錯移轉的次要複本，請以同步認可將次要複本的組態更新為自動容錯移轉目標。</span><span class="sxs-lookup"><span data-stu-id="5fba0-124">If there is not a secondary replica configured as automatic failover, update the configuration of a secondary replica to be the automatic failover target with synchronous commit.</span></span>  
  
-   <span data-ttu-id="5fba0-125">使用此原則確認資料處於同步處理狀態而且自動容錯移轉目標為 SYNCHRONIZED，然後解決可用性複本上的問題。</span><span class="sxs-lookup"><span data-stu-id="5fba0-125">Use the policy to verify that the data is in a synchronization state and the automatic failover target is SYNCHRONIZED, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fba0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fba0-126">See Also</span></span>  
 <span data-ttu-id="5fba0-127">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5fba0-127">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="5fba0-128">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5fba0-128">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
