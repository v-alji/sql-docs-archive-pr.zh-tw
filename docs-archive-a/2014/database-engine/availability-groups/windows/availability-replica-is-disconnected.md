---
title: 可用性複本已中斷連接 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1db92b8e73b6daaee7edf5042b1d73cfeb471d1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701920"
---
# <a name="availability-replica-is-disconnected"></a><span data-ttu-id="d5d5c-102">可用性複本已中斷連接</span><span class="sxs-lookup"><span data-stu-id="d5d5c-102">Availability replica is disconnected</span></span>
    
## <a name="introduction"></a><span data-ttu-id="d5d5c-103">簡介</span><span class="sxs-lookup"><span data-stu-id="d5d5c-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5d5c-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="d5d5c-104">**Policy Name**</span></span>|<span data-ttu-id="d5d5c-105">可用性複本連接狀態</span><span class="sxs-lookup"><span data-stu-id="d5d5c-105">Availability Replica Connection State</span></span>|  
|<span data-ttu-id="d5d5c-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="d5d5c-106">**Issue**</span></span>|<span data-ttu-id="d5d5c-107">可用性複本已中斷連接。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-107">Availability replica is disconnected.</span></span>|  
|<span data-ttu-id="d5d5c-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="d5d5c-108">**Category**</span></span>|<span data-ttu-id="d5d5c-109">**嚴重**</span><span class="sxs-lookup"><span data-stu-id="d5d5c-109">**Critical**</span></span>|  
|<span data-ttu-id="d5d5c-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="d5d5c-110">**Facet**</span></span>|<span data-ttu-id="d5d5c-111">可用性複本</span><span class="sxs-lookup"><span data-stu-id="d5d5c-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d5d5c-112">描述</span><span class="sxs-lookup"><span data-stu-id="d5d5c-112">Description</span></span>  
 <span data-ttu-id="d5d5c-113">這項原則檢查可用性複本之間的連接狀態。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-113">This policy checks the connection state between availability replicas.</span></span> <span data-ttu-id="d5d5c-114">當可用性複本的連接狀態為 DISCONNECTED 時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-114">The policy is in an unhealthy state when the connection state of the availability replica is DISCONNECTED.</span></span> <span data-ttu-id="d5d5c-115">否則原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5d5c-116"> 在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [可用性複本已中斷連接](https://go.microsoft.com/fwlink/p/?LinkId=220857) 。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica is disconnected](https://go.microsoft.com/fwlink/p/?LinkId=220857) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="d5d5c-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="d5d5c-117">Possible Causes</span></span>  
 <span data-ttu-id="d5d5c-118">次要複本未連接到主要複本。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-118">The secondary replica is not connected to the primary replica.</span></span> <span data-ttu-id="d5d5c-119">連接狀態為 DISCONNECTED。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-119">The connected state is DISCONNECTED.</span></span> <span data-ttu-id="d5d5c-120">這個問題可能是由於下列原因所造成：</span><span class="sxs-lookup"><span data-stu-id="d5d5c-120">This issue can be caused by the following:</span></span>  
  
-   <span data-ttu-id="d5d5c-121">連接通訊埠可能與另一個應用程式衝突。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-121">The connection port might be in conflict with another application.</span></span>  
  
-   <span data-ttu-id="d5d5c-122">加密類型或演算法不符。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-122">The encryption type or algorithm is mismatched.</span></span>  
  
-   <span data-ttu-id="d5d5c-123">連接端點已刪除或尚未啟動。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-123">The connection endpoint has been deleted or has not been started.</span></span>  
  
-   <span data-ttu-id="d5d5c-124">傳輸已中斷連接。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-124">The transport is disconnected.</span></span>  
  
## <a name="possible-solutions"></a><span data-ttu-id="d5d5c-125">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="d5d5c-125">Possible Solutions</span></span>  
 <span data-ttu-id="d5d5c-126">此問題的可能解決方案如下：</span><span class="sxs-lookup"><span data-stu-id="d5d5c-126">Following are possible solutions for this issue:</span></span>  
  
-   <span data-ttu-id="d5d5c-127">檢查主要複本與次要複本執行個體的資料庫鏡像端點組態，並更新不符的組態。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-127">Check the database mirroring endpoint configuration for the instances of the primary and secondary replica and update the mismatched configuration.</span></span>  
  
-   <span data-ttu-id="d5d5c-128">檢查通訊埠是否相衝突，如果是，則變更通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="d5d5c-128">Check if the port is conflicting, and if so, change the port number.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d5c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d5c-129">See Also</span></span>  
 <span data-ttu-id="d5d5c-130">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d5d5c-130">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="d5d5c-131">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d5d5c-131">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
